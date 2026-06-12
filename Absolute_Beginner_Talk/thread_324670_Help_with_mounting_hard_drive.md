---
title: "Help with mounting hard drive?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by scandalousartist on 2006-12-24
First off I'd like to say hi to everyone. I just downloaded Ubuntu today and have been experimenting with it's many features. I'm new to linux so please be patient with me.

I've pretty much have grasped all the basic features such as updating, locating files in the terminal, make file etc. I've even managed to get my NVIDIA Drivers to work hehe. The one problem I am having problems with is being able to see my Backup drive.

I originally came from Win2k pro and have 2 hard drives installed. I use my smaller drive to run my programs and my larger drive to back up my file. Now I know that most of the stuff I have on my Backup drive will be useless on Linux but i do have quite a few files I can use. I do both 3d and 2d art and have Blender, Gimp and jpg files on my backup drive that I would like to still be able to open. Unfortunately I'm not too linux savy and have no idea how I would be able to access these files from linux.

If anyone can explain how to mount the backup drive I have I would really appreciate the info. Please keep it as simple as possible, I'm not computer illiterate by no means but am still new to the terminal and getting around in linux. Thanks.

Dale

---

### Post by scoon on 2006-12-24
Hey there, 

If the other drive was plugged in during install, it probably got set up by the installer.  You can check to see what's mounted by either using mount or df -h with a terminal.  If the drive you are looking for is not mounted, you can start by reading man mount.

-scoon

---

### Post by bodhi.zazen on 2006-12-24
Mounting and permissions depends on the file system:

_Windows:_

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by scandalousartist on 2006-12-25
Thanks for the help. I managed to figure out how to mount my backup drive by following the info on those links.

Dale

---

