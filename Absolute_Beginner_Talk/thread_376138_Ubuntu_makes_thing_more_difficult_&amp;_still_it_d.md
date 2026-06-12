---
title: "Ubuntu makes thing more difficult &amp; still it doesnt work properly [Resolved]"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by reza81 on 2007-03-04
I got a new Toshiba 320 USB external HDD. I had to log it on to a M$ system to disable the passsword protection. off course it's not possible to write to NTFS. So, I Gparted it to ext3.
still no writing or executing promission!!!

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         272     2184808+  82  Linux swap / Solaris
/dev/hda2             273        2567    18434587+  83  Linux
/dev/hda3            2568        9729    57528765   83  Linux

Disk /dev/sdf: 320.0 GB, 320046346240 bytes
255 heads, 63 sectors/track, 38910 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       38910   312544543+  83  Linux

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14946   120053713+   7  HPFS/NTFS

``` 


edit: 
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             18145120   4978548  12244844  29% /
varrun                  387764       104    387660   1% /var/run
varlock                 387764         0    387764   0% /var/lock
procbususb               10240       220     10020   3% /proc/bus/usb
udev                     10240       220     10020   3% /dev
devshm                  387764         0    387764   0% /dev/shm
lrm                     387764     17580    370184   5% /lib/modules/2.6.17-11-generic/volatile
/dev/hda3             56625920  24529520  29219964  46% /home
/dev/sdf1            307639700    196768 291815708   1% /media/usbdisk
/dev/sda1            120053712 103959268  16094444  87% /media/FoShizzL


```

what can I do now?

---

### Post by annda on 2007-03-04
modify your fstab and make sure your drive gets the correct mount options if "defaults" isn't working.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

also, recursive chown and chmod (-R) might help.

---

### Post by aysiu on 2007-03-04
Try this:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by reza81 on 2007-03-04
thanks a lot!


I finaly understand :-)

---

