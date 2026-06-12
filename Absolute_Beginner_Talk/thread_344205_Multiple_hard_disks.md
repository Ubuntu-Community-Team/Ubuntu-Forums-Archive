---
title: "Multiple hard disks"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-01-22
Currently I have ubuntu 6.10 on one hard disk. I am looking to dabble with a few other distros, probably starting with fedora core 5/6. I want to keep my data (music, work etc) so a straight install (formatting the drive) is a last resort. I am in the process of acquiring a couple more internal drives and would like some opinions on how to procede.

The new drives will be second hand and formatted NTFS so firstly i would like to know how to format them as ext3 or other suitable filesystem.

Secondly, once installed is it better to transfer data to the "new" drive and format the main one, installing FC5 (or any other) or better to set the "new" drive as master and install to that one. I have no idea what sizes they will be yet.

Lastly should i just copy data to the "new" drive (i.e. my /home/user directory) and when installing new OS create multiple partitions on the "old" drive and transfer it back....Do all linux distros use the same filesystem allowing me to copy /home/user into fedora's file structure and have it work

---

### Post by j19sch on 2007-01-24
> **V-600 said:**
> The new drives will be second hand and formatted NTFS so firstly i would like to know how to format them as ext3 or other suitable filesystem.
You can do this while partitioning.

> Secondly, once installed is it better to transfer data to the "new" drive and format the main one, installing FC5 (or any other) or better to set the "new" drive as master and install to that one. I have no idea what sizes they will be yet.

Lastly should i just copy data to the "new" drive (i.e. my /home/user directory) and when installing new OS create multiple partitions on the "old" drive and transfer it back....Do all linux distros use the same filesystem allowing me to copy /home/user into fedora's file structure and have it work
Why don't you use a seperate partitionfor /home? That way you'll never have to worry about your data.
If you want to run several distributions you can even make a /data-partition in which you create /data/ubuntu-home and /data/fc-home and then link it so that Ubuntu and FC can find it. (There's a how-to on this forum somewhere). Then you can use the same username but have different settings in Ubuntu and FC.

Joep

---

### Post by mikewhatever on 2007-01-24
See here for multiple HDs [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
Gparted LiveCD lets you format partitions
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

