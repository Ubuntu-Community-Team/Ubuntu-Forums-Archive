---
title: "Windows and Ubuntu on same drive?"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by Delirious on 2005-05-23
Ok im a hardcore linux noob, but im really eager to learn. Two questions:

I have windows running on a drive that has two partitions on it, windows on one and the other is empty. Also have a second drive were everything else is stored/installed.

Is it possible to put ubuntu in the same drive as windows but in the other empty partition(23gb)?

Also will it run on ntfs? Id like to be able to share some files between windows and ubuntu.

---

### Post by bored2k on 2005-05-23
Is it possible to put ubuntu in the same drive as windows but in the other empty partition(23gb)?
Yes

Also will it run on ntfs? Id like to be able to share some files between windows and ubuntu.
Ubuntu wont run on NTFS, but you can share files between them.
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by stepper on 2005-05-23
Ubuntu & XP: [http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo)

---

### Post by f.prisson on 2005-05-23
> Is it possible to put ubuntu in the same drive as windows but in the other empty partition(23gb)? That should be no problem. Have a look at this howto: [http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo) 

You can read NTFS partitions, NTFS write support seems not to be enabled in the default kernel configuration: ```
grep -i ntfs config-2.6.10-5-386
``` ```
ONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
# CONFIG_NTFS_RW is not set
``` I don't know whether a special kernel with having enabled this is available. If not you have to recompile this modul for your kernel.

---

### Post by poofyhairguy on 2005-05-23
[QUOTE=f.prisson] NTFS write support seems not to be enabled in the default kernel configuration[/QUOTE]

Because its very unstable and it can easily trash four NTFS drive.

---

### Post by poofyhairguy on 2005-05-23
[QUOTE=f.prisson] NTFS write support seems not to be enabled in the default kernel configuration[/QUOTE]

Because its very unstable and it can easily trash your NTFS drive.

---

### Post by JimmyBEng on 2005-05-24
a better solution for sharing files is to create a FAT partition.  So use part of that 23gb for your ubuntu partion and make a part of it FAT32 and then both windows and ubuntu can access those files.  See the ubuntuguide for how to mount the FAT partion. (and how to read from your ntfs drive)

---

### Post by jsuen on 2005-06-08
[QUOTE=JimmyBEng]a better solution for sharing files is to create a FAT partition.  So use part of that 23gb for your ubuntu partion and make a part of it FAT32 and then both windows and ubuntu can access those files.  See the ubuntuguide for how to mount the FAT partion. (and how to read from your ntfs drive)[/QUOTE]
 sorry, just to clarify: will ubuntu work on fat32?
[http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx](http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx)
from the sounds of that article it alludes to not, or maybe i'm just not reading it right. :P

i've got ubuntu and xp both on the same drive (a slave drive, if it makes any difference). not sure if it can be set up like that but i'll have a crack too. :)

---

