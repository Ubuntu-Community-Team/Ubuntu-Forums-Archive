---
title: "no permissons"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Resistance on 2007-07-03
Hello,

I run Ubuntu 7.04 on an AMD 64 dual core processor. I have an external harddrive attached via usb 2. A LaCie 250Gb. I can access the files on this external drive (mostly music) but I can't seem to copy files to this external drive.

The error messag is:

You do not have permissions to write to this folder.

I am supposed to be root though, so why do I get this message and what can I do about it?

Thank you for your advice!

---

### Post by ghost_ryder35 on 2007-07-03
format the drive to FAT32 or download the NTFS writing ****

---

### Post by Rocket2DMn on 2007-07-03
If it is an ntfs drive, you need to have ntfs-3g installed (sounds like you must) as well as ntfs-config.  Then you need to enable writing to the drive with ntfs-config.
NTFS does not have "permissions" on a file-by-file basis, only access or no access to a drive.

---

### Post by Ek0nomik on 2007-07-03
> **Rocket2DMn said:**
> If it is an ntfs drive, you need to have ntfs-3g installed (sounds like you must) as well as ntfs-config.  Then you need to enable writing to the drive with ntfs-config.
NTFS does not have "permissions" on a file-by-file basis, only access or no access to a drive.

Formatting to a natively recognized file system is suggested though, rather than keeping NTFS.

---

### Post by Rocket2DMn on 2007-07-03
True, but it can be a major hassle, esp. if he has trouble accessing his files right now.
Ek0's option is best, but you will have to store your files on the drive somewhere else before you reformat so you can reload them afterward.  
Windows computers CAN read ext2/3 systems (natively recognized in linux) using the driver from [www.fs-driver.org](www.fs-driver.org) 
If you have the time and drive space, a backup and reformat is suggested, but not required.
I use an external ntfs drive with no problems, so it's really a matter of preference.

---

### Post by Inxsible on 2007-07-03
It might as well be a ownership issue on the mount point. Try installing the ntfs-3g drivers and if that does not work you will have to take ownership of the mount point to be able to write to the drive.
 
 
You can install ntfs-3g by Applications-->Add/Remove. Search for ntfs. Mark NTFS Configuration Tool for installation.
 
Then go to Applications-->System Tools --> NTFS Configuration Tool. Enable write support for internal and external drives.

---

