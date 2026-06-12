---
title: "can write to external hard disk, but can in Windows"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Roger D on 2007-12-06
Hi

I've had been using an external hard disk - a Western Digital My Book, with a FAT32 file system - for over a year with no problems. Suddenly, for no apparent reason, I can't write to it anymore. I thought that maybe it had failed, but when I connect it to Windows XP, all is well - I can add new files and change the names of files. 

So, the drive is OK, but seemingly some Ubuntu setting, I'm using Dapper Drake, has been changed.

Can anyone one tell me how to get my drive working properly again.

Regards

Roger D

---

### Post by banewman on 2007-12-06
Do you get an error message - if so, what is it?

---

### Post by Roger D on 2007-12-06
No, but if I try and copy a file to the drive, the copy option isn't available in the drop-down menu

---

### Post by banewman on 2007-12-06
Have you tried unmounting it and remounting.
That might help.
sudo umount /dev/sd?? 
sudo mount -v /dev/sd?? /mnt/???
where ?? is the options for your drive.

---

### Post by mahiyar on 2007-12-06
Maybe the drive has become read only? try copying the file using >>gksudo nautilus (you will run nautilus as root), if you succeed please post (copy paste) your fstab file >> gedit /etc/fstab

---

### Post by Roger D on 2007-12-06
Still can't copy, but here's gedit /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by mahiyar on 2007-12-06
Can you browse through the drive, i.e does ubuntu recognise the drive when connected?

---

### Post by lvleph on 2007-12-06
I had to install ntfs-config to be able to write to my ntfs external drive.

```
sudo apt-get install ntfs-config
```

That will allow you to change the permission on the drive to allow you to write to it.

I then unmounted the drive. Unplugged it and plugged it back in.

---

### Post by Roger D on 2007-12-06
Yes, I can open the drive, see and read all my files and folders, but I can't change anything

---

### Post by mahiyar on 2007-12-06
lvleph - Roger has a FAT32 drive no need for ntfs drivers !!

---

### Post by Roger D on 2007-12-06
Yes, and my point is that it used to work fine with a FAT32 file system

---

### Post by mahiyar on 2007-12-06
Maybe this link could help [https://answers.launchpad.net/ubuntu/+question/3620](https://answers.launchpad.net/ubuntu/+question/3620) , basically it talks about linux recognizing drive errors (power fail, remove w/o unmount etc) and making the disk read only to prevent further errors, to proceed do a fsck (after reading proper instructions) and maybe you can be happy in linux. Another short cut which I used to do with NTFS drive is to go back to windows mount and unmount the external drives properly and then try your luck in linux.

---

### Post by Roger D on 2007-12-06
Oh dear! fsck looks really scary. I tried the unmnount properly in XP idea, but it was no help.

One thing I've noticed - in the past I've had problems with this dirve if I failed to eject it properly. The way round this problem was to remove all references to the drive in /media - I ran rm on 'My' and rm -r on 'My Book'. However, now when I do an 'ls' on meda, the 'My' file isn't there anymore. Is this telling me anything?

---

### Post by lvleph on 2007-12-07
> **mahiyar said:**
> lvleph - Roger has a FAT32 drive no need for ntfs drivers !!

Yeah I am dumb. I guess I missed that.

---

