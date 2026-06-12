---
title: "media drive"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by synndicate13 on 2008-04-15
i have no idea how to mount my hard drives at all. i have a swap partition for running windows and ubuntu but i dont know if i am really supposed to be able to get to my harddrives that are running on windows or not. and if i am, how? and can i change/edit the files in them? or do i have to format them for them to work on ubuntu? im lost ):

---

### Post by spiderbatdad on 2008-04-15
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
That is for mounting the windows partition...see link at bottom to enable read/write...hint: install ntfs-3g...```
sudo apt-get install ntfs-3g
```

---

### Post by Shazaam on 2008-04-15
Ubuntu usually auto-mounts most drives/partitions. It may have problems with external drives but that is usually due to operator error. As far as drives/partitions go, Gutsy has NTFS and FAT32 (Windows) read/write access enabled by default.
Think of / as C: in Windows. Everything after / is a folder/directory or file. So your home folder would be /home. Anything inside your home folder would be /home/yourusername/whatever
You can mount a drive almost anywhere but there are standard places to do this. /media and /mnt are used for this. To mount a drive/partition you would use a code similar to this in terminal....
```
sudo mount /dev/hda5 /media
```
This would mount the hda5 partition in the /media folder.
To unmount it you would use a code similar to this......
```
sudo umount /dev/hda5
```
(note- umount is not a typo)
 To find out your partition info you would run this in terminal.....
```
sudo fdisk -l
```
(small L)

These links might help a little.........
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[https://help.ubuntu.com](https://help.ubuntu.com)
[http://www.linuxcommand.org/learning_the_shell.php#contents](http://www.linuxcommand.org/learning_the_shell.php#contents)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

---

### Post by Inxsible on 2008-04-15
If you are using Gutsy, then ntfs support should be built in. and I think you probably mean a "shared" drive rather than "swap"

---

### Post by synndicate13 on 2008-04-16
i appreciate all the help! and no i meant swap partition, not a shared drive, which is what 2 of my drives are on windows. but thanks. X)

---

