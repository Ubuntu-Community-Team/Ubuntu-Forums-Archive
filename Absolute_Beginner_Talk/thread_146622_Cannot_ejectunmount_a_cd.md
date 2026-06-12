---
title: "Cannot eject/unmount a cd"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by kostyabkg on 2006-03-18
Hello,
First of all I wanted to say thank you for creating Ubuntu - this is the most user-friendly Linux I've ever seen.
I have one problem, though: when I try to eject a cd-rom it says:

umount: /dev/hdb mount disagrees with the fstab
eject: unmount of `/tmp/disks-conf-hdb' failed

What's the crack here?
Also why when I install something or when Synoptic Package Manager is loading something, the system becomes very unresponsive, mouse movements become jerky, if I am listening to the music, it's breaking up. Maybe I have to set-up a DMA mode or something, I am running on PIV 3.2 GHz, so these problems shouldn't occure in my opinion. Or maybe I am wrong?

Thank you for help!
Kostya.

---

### Post by aysiu on 2006-03-18
Can you post the output of these two commands? ```
cat /etc/fstab
df -h
```

By the way, you can usually eject by typing ```
sudo eject /dev/cdrom
```

---

### Post by kostyabkg on 2006-03-18
kostya@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

*************************************

kostya@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  2.3G   15G  14% /
tmpfs                 252M     0  252M   0% /dev/shm
tmpfs                 252M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
************************************

By the way, after rebooting everything started working OK. Prior to that I installed a whole bunch of software, maybe something locked the CD?

---

### Post by aysiu on 2006-03-18
It's possible something locked the CD.
In the future, ```
sudo eject /media/cdrom0
``` may work if you're stuck.

Most of the time, though, you can right-click on the CD icon and select "eject."

---

