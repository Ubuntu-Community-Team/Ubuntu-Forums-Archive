---
title: "completely befuddled"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by stained_glass_masquerade on 2006-01-19
I'm completely new to ubuntu.  I've spent my whole life a slave to windows and I couldn't take it anymore.  Anyway, here's one of my many problems.  I have two hard drives.  One is 60 GB and the other is 149 GB.  I have an extensive music collection that I like to keep on my larger hard drive.  However, since I installed linux I can't seem to get my computer to acknowledge my larger hard drive.  It must have been due to an error I made during the installation process.  Other than that I'm enjoying the change to linux.

---

### Post by griz on 2006-01-19
have you mounted the second hard drive?

---

### Post by stained_glass_masquerade on 2006-01-19
well in my disk manager it acknowledges both hard drives.  i'm not sure if that means it was mounted or not.

---

### Post by paulmilliken on 2006-01-19
[QUOTE=stained_glass_masquerade]I'm completely new to ubuntu.  I've spent my whole life a slave to windows and I couldn't take it anymore.  Anyway, here's one of my many problems.  I have two hard drives.  One is 60 GB and the other is 149 GB.  I have an extensive music collection that I like to keep on my larger hard drive.  However, since I installed linux I can't seem to get my computer to acknowledge my larger hard drive.  It must have been due to an error I made during the installation process.  Other than that I'm enjoying the change to linux.[/QUOTE]

Do you know if your second hard disk drive is formated at FAT32?  Other options are ext3, ntfs, reiserfs etc.  If your drive is formated as, say ext2, then follow steps 5 and 6 of [http://www.linuxgazette.com/issue38/cooper.html](http://www.linuxgazette.com/issue38/cooper.html)

Also, please post the contents of your /etc/fstab file as it may already be mounted.

---

### Post by griz on 2006-01-19
Ok, if it recognises the disk, the next question would be, what is the file format on the second disk?  If you create a folder for the disk by doing "sudo mkdir /media/*whatever_you_want_to_call_it*" then sudo mount -t *filesystem* /dev/hdb /media/*whatever_you_want_to_call_it*.  Filesystems are vfat for dos and early windows systems or ntfs for later systems.

Griz.

---

### Post by dueY on 2006-01-19
I'm guessing your Windows drive is NTFS.  If you want it to show up (be mounted) every time you boot into Linux do this

```
sudo mkdir /media/windows
```
Then
```
sudo gedit /etc/fstab
```
Then add this to the end of fstab
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```
Go to disk manager and replace the "hda1" with whatever your Windows drive is called.

---

