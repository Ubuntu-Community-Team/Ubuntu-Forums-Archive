---
title: "Internal backup HDD - which filesystem to use?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Malcy on 2007-10-28
I have a spare HDD attached to my PC (Ubuntu 7.10) via the ide controller which I want to use as a automatic backup with sbackup and also to store partimage images.

The question is, which FS to use - ext2, ext3, ntfs, reiser or fat32?

I have an external usb HDD which I use on both Linux and Windows systems and is fat32 for this reason. However the 4GB file size limit may be a problem with partimage images when stored on the spare HDD in question. NTFS will be too problematic, Reiser I don't know anything about which leaves ext2 and ext3. It will only be read from a Linux OS.

Any advice?

---

### Post by Qwerty_ on 2007-10-28
NTFS is nolonger a problem in linux.

Just install ntfs-config and you can solve your issues easily.

---

### Post by insane_alien on 2007-10-28
XFS is a good choice as it handles large files very well and has a windows driver available. just be careful to shutdown properly and keep it unmounted when not in use or you could end up with problems due to delayed allocation.

---

### Post by louieb on 2007-10-28
Don't know what is best. But my Linux desktop has a 2nd drive I use for backup  (I use  sbackup and partimage too). Its formated ext3. It's been trouble free.

---

### Post by Incense on 2007-10-28
It really depends on what systems are using it. If you are using it to backup windows and MAC files, and they are not too big, then FAT32 is a good option as they all read it just fine, even though FAT32 kind of sucks...If you are backing up DVD ISO's though, then you may want NTFS as it can handle large files better then FAT. If it is all Linux though, then EXT3 is a good option.

---

### Post by Malcy on 2007-10-28
Thanks for the replies

As I said in the original post, it will **only** be used by a Linux OS as it is an internal drive for backup storage. I have an external USB HDD formatted to FAT32 for use across systems. If I put partimage files on the backup drive, they may be above 4GB.

I am still somewhat unsure which is best to use as in all your kind replies, the following have been recommended: FAT32, XFS, NTFS, ext3. What are the potential problems with ext3?

:confused:

---

### Post by insane_alien on 2007-10-28
the only problems with ext3 are that for large files(if you are storing images of drives then they will definitely be large) it is very slow. XFS is best at this.

i'm running a few drives on XFS(one is a backup drive) and i have had no problems that weren't because of me being stupid and disconnecting the power while it was writing because i triped over the computer.

---

