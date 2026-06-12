---
title: "got a problem"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by fix3r on 2007-01-03
Well I was stupid enough to install vmware by a rpm and not by source.

There was an error and I guess vmware server didn't get to finish install so now when ever I type in "vmware" it gives me an error. I am wondering if there is a way to remove this error so I can continue and go try the installation (by source this time) again.
```
fix@b0x:~/Desktop$ vmware
/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found
```

I also would like to know how I would go about un-installings things I have installed in the past from compiling from source. If you have any details regarding this please care to share.

Thank you for your time.

---

### Post by rlozano on 2007-01-03
try sudo aptitude remove --purge vmware.

---

