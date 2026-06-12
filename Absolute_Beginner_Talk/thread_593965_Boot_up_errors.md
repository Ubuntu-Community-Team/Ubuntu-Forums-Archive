---
title: "Boot up errors"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-10-27
When I try booting Gusty, the Usplash image shows up fine, and then when you would expect GDM to start, I get these errors:

```
/etc/init.d/rc: 2: usplash_write not found
/etc/init.d/rc: 2: sed: not found
[repeats above line about 15 times]
init: unable to execute "/bin/sh" for rc-default: no such file or directory
init: rc-default main process (4400) terminated with status 255
```

What does all that mean?

Thanks.

---

### Post by Yes on 2007-10-27
Update:  When I boot in recovery mode, and start GDM from the command line, I can log in normally.  Then when I log in, I get the error "Failed to initilize HAL!", and then a few moments later my mouse stops working and I have to do a hard reboot.

---

