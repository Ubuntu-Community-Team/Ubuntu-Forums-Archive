---
title: "Remove AVG"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by eekfonky on 2007-04-18
I have tried to remove AVG as it doesn't like ubuntu, but I have had no success. I have even tried:
$ sudo dpkg --remove --force-all avg75fld

and all I get is:

(Reading database ... 153044 files and directories currently installed.)
Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 5007: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75fld

Any ideas?

---

### Post by Perfect Storm on 2007-04-18
You have to kill AVG process (avgupdate I think) before removing it.

---

