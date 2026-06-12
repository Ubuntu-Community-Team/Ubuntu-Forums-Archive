---
title: "sudo aptitude upgrade question"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by BHelts on 2007-06-03
i just did a fresh install of feisty after giving debian a try, so as i was doing some updating, i did```
sudo aptitude upgrade
``` and got this:
```
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-generic 
The following packages have been kept back:
  linux-headers-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```
is there a way to force the upgrade through aptitude? 
thanks in advance for your help.

---

### Post by Inxsible on 2007-06-03
Those 3 packages are you kernel packages. If you are logged into that kernel, they cant be upgraded as kernel stays in memory as long as the OS is up and running

---

### Post by H3g3m0n on 2007-06-03
If that was the case it would be impossible to update the kernel.

The kernel being in memory doesn't stop a kernel upgrade, it just won't take effect until the next reboot. You might also break (until reboot) some drivers/modules if they are different in the kernel upgrade.

Try 'apt-get dist-upgrade' instead, or see if you can get it to work though the GUI application (assuming your using a GUI)

---

### Post by Seisen on 2007-06-03
Actually to force them you can put this in the terminal.

```
sudo aptitude dist-upgrade
```

---

### Post by BHelts on 2007-06-03
thanks a lot for the information.  i appreciate it.

---

