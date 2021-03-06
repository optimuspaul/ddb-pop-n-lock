ddb-pop-n-lock
============

A simple reasonable lock for AWS dynamodb.

Use
============

```
from ddblocker import DDBLock

lock = DDBLock(key="LOCKTHISWAY!", table_name="my-fancy-locks-table", region_name="us-east-2")
with lock:
    # do some things
    pass

```

Lock will raise `LockFailedError` if the lock could not be aquired. By default there is a 30 second TTL on locks. I believe this to be reasonable for use within lambda functions when your timeout is 30 seconds. Set `max_live` on the lock to extend that assumption. Note that `max_live` is a value that is checked when attempting to aquire a lock and not set when locks have already been aquired.


License
============

The MIT License (MIT)

Copyright (c) 2016 Paul J DeCoursey, Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
