---
title: "[GUIDE]Getting suspend + touchpad  to work properly on 11.04"
date: 2011-05-27
forum: Apple Hardware Users
---

### Post by Apewall on 2011-05-27
Every macbook on the wiki lists the suspend on close breaking the touchpad when it resumes and this has yet to be fixed.  I've seen a number of users mention this here on the apple forum as well with no answer.

After some digging when i realized the module section of acpi-support did nothing to fix this I found a script which will load the driver after resume properly.  The culprit is the bcm5974 module.  Found here is the original script for fedora [http://nareshv.blogspot.com/2009/06/fedora-11-64-bit-final-on-macbook-pro.html](http://nareshv.blogspot.com/2009/06/fedora-11-64-bit-final-on-macbook-pro.html)

There are a few launchpad issues already open for this bug for mactel but none are listed as being worked on.

Create the script in suspend.d
```

sudo nano  /usr/lib/pm-utils/suspend.d/02touchpad

```

Paste the following
```

#!/bin/bash

if [ -e '/usr/lib/pm-utils/functions' ];then
. /usr/lib/pm-utils/functions
fi

suspend_bcm5974() { /sbin/rmmod bcm5974; }
resume_bcm5974() { /sbin/modprobe bcm5974; }

case "$1" in
    suspend|hibernate)
        suspend_bcm5974;
        ;;
    thaw|resume)
        resume_bcm5974;
        ;;
    *)
        ;;
esac

exit $?
```

Make the script executable
```
sudo chmod 755 /usr/lib/pm-utils/suspend.d/02touchpad
```


After this I have not had an issue with the touchpad after resuming from suspend on my Macbook Pro 4,1.  Let me know if it resolves the issue for you as well.

---

