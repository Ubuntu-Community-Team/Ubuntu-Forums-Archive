---
title: "Permissions Trouble"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by sven_henson on 2007-03-01
I am trying to change the permissions of both my file system and external hard drive from read to read/write. However when doing this (i have been using preferences) i am told they could not be changed. Any suggestions

Thanks
Sven

---

### Post by taurus on 2007-03-01
What directory on your system do you plan to change the permission?  Be real careful with it because if you change the wrong one, you would crash your machine and only reinstall would probably save it.

What filesystem is your external harddrive anyway?

---

### Post by sven_henson on 2007-03-01
Well i wanted to change my external hard drive's permissions specifically. How can i find its file system, it should be formatted as a standard windows external drive as that is what i had been previously using it with. Any help is appreciated.


CHeers
Sven

---

### Post by Mr. C. on 2007-03-01
Sven,

You're confusing concepts.

You mount file systems.  You change permission on files and directories.

Yes, file systems can be mounted read-only as well.

It sounds like you have a Windows drive.  It is either formated as FAT or NTFS.

You can mount either file system, but as far as I am aware, writing to NTFS file systems from *nix is still weak at best.

Tell us what type of file system is on the disk, and what you want to do with it.

if you want to erase the disk, and make it a linux file system, you can format the drive, and mount the device onto the linux file system.

Give the helpers here more information!

---

### Post by taurus on 2007-03-02
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
And it would tell you either it's ntfs or vfat/fat32.

---

### Post by agiamba on 2007-03-02
I have an internal-hd partition and an external hd, both formatted as Fat32 and I don't have read/write permissions. How do I change this, everytime I right-click and change it, it reverts instantly. I need help!?

---

