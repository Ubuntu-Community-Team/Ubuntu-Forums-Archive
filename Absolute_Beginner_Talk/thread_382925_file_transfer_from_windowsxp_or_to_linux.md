---
title: "file transfer from windowsxp/ or to linux"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by daddydoc on 2007-03-12
1. How do I see my ubuntu computer's file system from windows, so I can transfer files from windowsxp to ubuntu?
2. How do I see my windowsxp computer files, so I can transfer files from my ubuntu computer to windowsxp computer?

Thanks in advance

daddydoc

---

### Post by punx45 on 2007-03-12
I can't give you step by step instructions, because I don't use it, but I can tell you that you want to look into 'SAMBA.'

---

### Post by bruenig on 2007-03-12
1. You can use the driver from [fs-driver.org]("http://fs-driver.org/")

2. It depends. If it is ntfs, there is no native way to write to it in ubuntu. There is a driver that is said to allow you to do it though. Information [here]("http://www.ubuntuforums.org/showthread.php?t=217009"). If it is fat32, then it should be natively supported.

---

### Post by arron on 2007-03-12
samba is for network shares, do you mean the physical drive on the pc?  if so try

[http://www.ubuntuforums.org/showthread.php?t=250866&highlight=read+ntfs](http://www.ubuntuforums.org/showthread.php?t=250866&highlight=read+ntfs)

or

[http://www.ubuntuforums.org/showthread.php?t=373935&highlight=read+ntfs](http://www.ubuntuforums.org/showthread.php?t=373935&highlight=read+ntfs)

a search of ntfs on here will show many more results.

If it is over the network goto System -> Administration -> Shared folders and set up a share.  Windows right click the folder and select share.

---

### Post by qpwoeiruty on 2007-03-12
smbpasswd -a username
then you can choose the folder to share in system/administration/shared folders
username/password is the login credentials that you use from the windows machine.

in xp, just right-click on a folder, go to properties/sharing and choose a share name for it

you can access them by \\computername\shared folder\ or by places/network servers... in ubuntu or network places in xp

---

### Post by freebird54 on 2007-03-12
The answer depends on whether the Windows files are on the same computer, or a different one.  If there are 2 separate systems networked, then Samba is the answer.  If you are running a dual-boot, then access from Ubuntu to Windows is automatic if your Windows run on a VFAT filesystem, and not too difficult if you are running on the NTFS filesystem.  Windows can also run an "explorer" program to read from a standard Ubuntu drive.

If any of this sounds confusing - please say so and someone will be glad to explain or go into detail to get you going....

---

