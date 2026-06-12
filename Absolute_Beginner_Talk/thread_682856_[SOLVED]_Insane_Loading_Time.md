---
title: "[SOLVED] Insane Loading Time"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by on4c1d on 2008-01-30
Hi there :)
I installed ubuntu for the first time like 2 months ago. This is also my first attempt to use any linux release.
Everything worked perfect till yesterday. For some reason Ubuntu takes ages to load after i choose which operating system to use in grub. I tried ctrl+alt+f1 and notice it stops for at "Loading, please wait" message for 3-4 minutes. At that time i notice full disk activity (at least the hdd led is on). After that pause everything seems to load normally.
I can definately re-install since there is nothing i am gonna lose if i format the disk but i would prefer to take my chances in working around this problem :)
I can't remember of doing installing anything or changing some option before the problem occured :(
Any ideas ?
Thanx alot :)

---

### Post by emarkd on 2008-01-30
Does it still do it?  Every 30 boots or so, Ubuntu will run a checkdisk type program to make sure your journaled filesystem is healthy.  It takes quite a while to run.

---

### Post by philinux on 2008-01-30
fsck is the file system check utility which runs every 30-40 boots depending on the size of the file system. All is well as long as it finds no errors. Even then it usually fixes them.

If you want to know how many boots you've done and how many boots when it's set to trigger do this command in a terminal.

```
sudo tune2fs -l /dev/sdax
```    (x being your linux drive usually 1 or 2 etc)

---

### Post by on4c1d on 2008-01-30
!!! thanx for the quick response guys. I am gonna try it now.

---

### Post by on4c1d on 2008-01-30
How do i know the number of my linux drive ? I am new to all this :confused:
I tried sda0, sda1 & sda2 but doesnt seem to work.
Btw even if the long loading time was caused by this check disk i guess it should have returned to normal after afew boots right ? I have done like 20 or 30 so far but nothing has changed :(

---

### Post by emarkd on 2008-01-30
You can find all of your disks by doing:

```
fdisk -l
```

and yes, the long boot time should only happen once and then go away for 30 boots or so

---

### Post by philinux on 2008-01-30
> **on4c1d said:**
> How do i know the number of my linux drive ? I am new to all this :confused:
I tried sda0, sda1 & sda2 but doesnt seem to work.
Btw even if the long loading time was caused by this check disk i guess it should have returned to normal after afew boots right ? I have done like 20 or 30 so far but nothing has changed :(

Use copy and paste to put the commands into the terminal. And post the results of each.

```
sudo fdisk -l

cat /etc/fstab
```

From your new info I doubt it's fsck. Click the link below for gutsy known bugs. One is long boot up times.

---

### Post by on4c1d on 2008-01-30
Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20fd20fd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4661    37439451   83  Linux
/dev/hdb2            4662        4866     1646662+   5  Extended
/dev/hdb5            4662        4866     1646631   82  Linux swap / Solaris
on4c1d@Acid:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e16349db-1c93-4b1f-a144-769a0f335865 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=93b1a28a-092d-4a49-94a4-564eb2c62079 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

so i guess my linux disk is hdb1 :D

---

### Post by on4c1d on 2008-01-31
Yesterday i noticed fsck is not the problem. The long waiting time occurs even before the check, after i choose operating system I see the messages: 
Starting Up...
Loading...
Pease wait...
After 3 or 4 minutes ubuntu starts loading :(

---

### Post by emarkd on 2008-01-31
Did you check [this]("http://ubuntuforums.org/showthread.php?t=595825") as suggested by philinux?  There's good information there about long boot times...

---

### Post by on4c1d on 2008-01-31
yes i did :( unfortunately my problem is very different

---

### Post by on4c1d on 2008-02-07
Ok, problem solved 
Insanely stupid of me but the ide cable was not fully plugged into the mobo causing the disk to be semi-operational. Strange though, i always thought that in that case the hd would not work at all :P

---

