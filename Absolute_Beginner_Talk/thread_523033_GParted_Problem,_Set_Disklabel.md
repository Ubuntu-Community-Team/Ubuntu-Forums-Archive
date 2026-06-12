---
title: "GParted Problem, Set Disklabel"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-08-11
Yeah, I was making some different partitions on my 1st drive, and wanted to change them back,
I still have XP on drive 1 , Ubuntu on drive 2 , and can access either OS, the problem is that I can't
use GParted to increase the partitions back on drive 1.  I get this, which says it'll destroy all data on
hda1, which I don't relish doing.

---

### Post by Pragmatist on 2007-08-11
Have you read this yet?
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Drakkor on 2007-08-11
I have resized partitions before, but now GParted shows [COLOR="Red"]no[/COLOR] partitions at all on drive 1, I know there are because XP is on there , and I can dual-boot Ubuntu/XP

---

### Post by Pragmatist on 2007-08-11
Please give us a screenshot of gparted showing the partitions.

Try this in a terminal and post the output here:

```
mount
```

After you type the following command, you will see a menu.  Just type 'p' for 'print' and then post the output here.  Quit by typing 'q'
```
sudo fdisk /dev/hda
```

---

### Post by Drakkor on 2007-08-11
drakkor@Ubuntu-Fiesty:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sdb3 on /media/sdb3 type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
drakkor@Ubuntu-Fiesty:~$ 

And I was running the GParted Live disc, so I guess I'll have to get it in synaptic to post a screenshot. :)

---

### Post by Drakkor on 2007-08-11
Here we go;

---

### Post by Pragmatist on 2007-08-11
[COLOR=Silver][COLOR=Black]Edit: Nevermind these questions: [/COLOR]Is Ubuntu on sdb and Windows on sda ?  They are on separate hard drives?


[/COLOR]

---

### Post by Pragmatist on 2007-08-11
You are running gparted from a LiveCD or from Ubuntu?  In either case, is /dev/sda mounted?  If so, what happens if you run gparted after you unmount /dev/sda?

---

### Post by Drakkor on 2007-08-11
Thanks for trying to help, Pragmatist Happens with both live disk,and Ubuntu, here's the system montitor: as said I have XP on sda1, drive 1,and Ubuntu on sdb1 drive 2, and  still can dual-boot
both systems ! ? :confused:

---

### Post by Pragmatist on 2007-08-11
> **Drakkor said:**
> Thanks for trying to help, Pragmatist Happens with both live disk,and Ubuntu, here's the system montitor: as said I have XP on sda1, drive 1,and Ubuntu on sdb1 drive 2, and  still can dual-boot
both systems ! ? :confused:
What happens if you unmount /dev/sda before running gparted?

---

### Post by Drakkor on 2007-08-11
Not exactly sure how to unmount the whole sda drive ?

---

### Post by Pragmatist on 2007-08-11
> **Drakkor said:**
> Not exactly sure how to unmount the whole sda drive ?
```
sudo umount /dev/sda
```

---

