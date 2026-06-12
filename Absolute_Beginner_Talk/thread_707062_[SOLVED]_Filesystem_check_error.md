---
title: "[SOLVED] Filesystem check error"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by oatts on 2008-02-25
While booting Ubuntu, it fails to do a filesystem check, and this is my fsck:


Log of fsck -C -R -A -a 
Sun Feb 24 22:32:03 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=e1d9b2be-0155-4512-9b68-7eba0f56dbdf'
fsck died with exit status 8


what should I do?

Thanks!!

---

### Post by plucky on 2008-02-25
> fsck.ext3: Unable to resolve 'UUID=e1d9b2be-0155-4512-9b68-7eba0f56dbdf'
fsck died with exit status 8

This problem is usually caused by the **UUID** in **/etc/fstab** not matching the UUID on disk.

When the system stops during the boot, press "enter" and then CTRL-D and it should continue to boot.

After you login open a terminal and type : ```
blkid
``` and then ```
cat /etc/fstab
```
Compare the UUID from the blkid command which is the correct UUID to the UUID's in the /etc/fstab file. One of them will be different i.e the one with the UUID=e1d9b2be-0155-4512-9b68-7eba0f56dbdf.

You then need to edit the /etc/fstab file after making a copy of it with ```
sudo cp /etc/fstab /etc/fstab.backup
``` and the edit the /etc/fstab file with ```
gksudo gedit /etc/fstab
``` and replace the incorrect UUID with correct value.

Clear as mud

Good luck

---

### Post by addisor on 2008-02-25
You sound like a /etc/fstab specialist, I've managed to wreck my FSTAB.

I edited the sda1 line to change ro to rw (instead of the dvd drive line )and now the computer won't boot. when i try a nano edit in recover mode its says read only and won't let me rectify my error!! any idea's

---

### Post by plucky on 2008-02-25
addisor,

I am no specialist but had the same problem as the OP,and that was how I fixed it.

Have you tried the Live CD,as your system is mounting your sda1 partition as read only so won't allow write access.You shouldn't have that problem with the live CD.

Always make a backup before editing system files.I know I sometimes forget as well.

Good luck

---

### Post by addisor on 2008-02-25
Where do i find etc/fstab for the problem install. If i run nano or gedit the fstab for the live cd comes up.

---

### Post by plucky on 2008-02-25
addisor

Goto Places > Computer and double click on the drive that contains fstab.It should now show up on the desktop.

Open a terminal and use ```
gksudo nautilus
``` a window should open.Click on**Filesystem > Media**.You should see your partition.Double click on it and then navigate your way to /etc/fstab. Double click on fstab and it should open with Gedit editor with sudo privileges. Make your changes and save.

Right click on desktop icon and dismount Now reboot.Again be careful

Good luck

---

