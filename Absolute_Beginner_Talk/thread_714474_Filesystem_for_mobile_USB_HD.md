---
title: "Filesystem for mobile USB HD"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by apokkalyps on 2008-03-03
So I bought this 750gb hard drive at frys for $160.  I've always been one to have partitions out the wazoo, but I dumped my old system and now keep everything on this drive.  When I installed ubuntu 7.10 I realized that the NTFS filesystem can cause problems, which is what I have.  I go back and forth between my windows pc and my linux pc with these files on this drive, so they have to both be able to read the file system.  And I want to be able to take it to my friends house and copy files with them, so it really needs to be readable by OEM windows.  
NTFS is causing problems because linux doesnt like to mount an NTFS partition that wasn't properly unmounted, and as far as I can tell, windows doesn't give you the option to eject/unmount a USB HD, only thumbdrives and such.  So you have to force the mount on ubuntu, and then it just causes hell.  Right now I have one mount /media/gigsofgoodness that wont go away and when I reconnect it can only mount as /media/gigsofgoodness_ 
What type of file system do you suggest I put on my USB drive to simplify this?  fat32?

---

### Post by jakl_53 on 2008-03-03
From what I have heard fat32 would be your best bet. I haven't messed around too much with partions and such but I read somewhere that it causes a lot less problems.

---

