---
title: "[SOLVED] trying to delete my NTFS partition, change it to reiserfs, and remount it"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by energy. on 2008-04-07
I'm using ubuntu as my only OS, but when I first set it up, I had a disk with a NTFS partition on it containing all of my music and movies.  I have since backed up all of the information on that disk and am trying to format it as reiserfs and remount it somewhere on my computer.  I opened up gparted and deleted the NTFS partition.  I then created a reiserfs partition the entire size of the disk.  Now I need to mount the disk to my filesystem so I can use it but don't know how to do that.  This is where you step in.  

I'd ideally like to mount it to /home, but I'm not sure how that'd work out since /home already exists.

---

### Post by bsharp on 2008-04-07
You would probably want to mount it to /media/{yourdrivename} so that an icon will pop up on the desktop (like when you insert a usb drive).   To mount it automatically, you need to add the drive to /etc/fstab 
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by energy. on 2008-04-07
> **bsharp said:**
> You would probably want to mount it to /media/{yourdrivename} so that an icon will pop up on the desktop (like when you insert a usb drive).   To mount it automatically, you need to add the drive to /etc/fstab 
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I followed that guide. . .and when it came time to mount the drive, I got this 

```
fitz@hugeevilrobot:~$ sudo mount /dev/sdb /space
mount: you must specify the filesystem type
```

---

### Post by energy. on 2008-04-07
ok. this is fixed.  I have the partition mounted now.

---

### Post by piousp on 2008-04-07
did you specified the reiserfs on the command???
I'hve never used it (mount), so its good to know how it works.
Guess you can mark the thread as "solved" :)

---

