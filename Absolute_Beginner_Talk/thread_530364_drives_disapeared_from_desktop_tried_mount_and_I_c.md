---
title: "drives disapeared from desktop tried mount and I can't seem to make it work"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by skidkid87 on 2007-08-20
I tried searching the forums for answers but I can't seem to find what I wanted to fix the problem

my two hard drives (sda1, sda2) disappeared after just like that, poof, I don't know why, they're present in media but just 2 empty folders and this appears when I write "sudo fdisk -l" :

ramy@ramy-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16129   129549466    7  HPFS/NTFS
/dev/sda2           18740       19457     5767335    7  HPFS/NTFS
/dev/sda3           16130       18739    20964825    5  Extended
/dev/sda5           16130       17434    10482381   83  Linux
/dev/sda6           17435       17695     2096451   82  Linux swap / Solaris
/dev/sda7           17696       18739     8385898+  83  Linux

Partition table entries are not in disk order

the drives are clearly there but I can't reach them tried mounting them manually but it kept telling me I don't have the permitions to view them while I'm the only account on this laptop


this appears in GParted for the first main partition:

File system: ntfs
Size : 123.55 GB
Flags : boot

path : /dev/sda1
status : not mounted

then there's a warning saying : "unable to read the contents of this file system, because of this some operations may be unavailable", "did you install the correct plugin for this filesystem ? ".

the other drive has similar output

help me out here plz

thanks in advance

---

### Post by jw5801 on 2007-08-20
You need to mount them before you can access them. Since they're ntfs make sure you have the ntfs driver's loaded: ```
sudo apt-get install ntfs-3g
```
then run this to mount them ```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```
Then the equivalent to mount the second partition/drive.

---

### Post by Lucifiel on 2007-08-20
Did you try installing ntfs-3g and then checking "support for internal drives"?

---

### Post by skidkid87 on 2007-08-20
I have a similar driver called ntfs configuration tool and it seemed to work fine for a wile but I don't know what made my drives disappear

---

### Post by skidkid87 on 2007-08-20
ok I got them back now, I tried mounting them but it told me to cleanly shutdown vista so I did (although vista was hibernated) and it worked

---

### Post by jw5801 on 2007-08-20
That's because Vista still had them mounted... you can't have 2 OS's trying to mount the same filesystem at once!

---

