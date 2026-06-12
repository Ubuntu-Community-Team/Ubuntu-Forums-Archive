---
title: "Mounting XP in ubuntu permanently :s"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by wobniarpro on 2007-04-03
[B]Hi all


i am new to ubuntu..

I want to mount my XP in ubuntu to listen music

i followed this [http://www.ubuntuforums.org/showthread.php?t=390192](http://www.ubuntuforums.org/showthread.php?t=390192) link..

at the end guy says create hda1 in media but icant create that...

i tried

[http://www.ubuntuforums.org/showthread.php?t=390192](http://www.ubuntuforums.org/showthread.php?t=390192)

$ cd /
$ cd media
$ mkdir hda1
 and it says,,,, mkdir: cannot create directory `hda1': Permission denied


btw: i have edited  fstab file putting at end /dev/hda1 /media/hda1 ntfs defaults 0 0
[/B]

---

### Post by taurus on 2007-04-03
```
**sudo** mkdir /media/hda1
```

---

### Post by wobniarpro on 2007-04-03
[B]thanks


it will load windows automatically b now on?

[if i do that _] [/B]

---

### Post by taurus on 2007-04-03
Yes, if you have an entry in /etc/fstab for it.

p.s.  And what's with the bold text anyway?

---

### Post by dfreer on 2007-04-03
Well, first off do you know if your XP hard drive is /dev/hda1? you will need to make sure that your XP partition is /dev/hda1 because it is pretty much different on everybody's system, depending on whether they use SATA/IDE drives, partitioning schemes, etc.

Also, to make a directory in /media you need root permissions. Try using:
```
sudo mkdir /media/hda1
```

---

### Post by bigee1212 on 2007-04-03
This is how to do it properly:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

