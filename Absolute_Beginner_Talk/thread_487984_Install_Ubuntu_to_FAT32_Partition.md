---
title: "Install Ubuntu to FAT32 Partition"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by tap52384 on 2007-06-29
To those who can help:

Without the hate that comes against all things Microsoft, I was wondering if it were possible to install Ubuntu to a FAT32 partition as the root file system.  While attempting to install Ubuntu 7.04, I tried to specify FAT32 as the file system for the root file system (mount point "/") but then I received an error message:

Invalid file system for this mount point

The file system type fat32 cannot be mounted on /, because it is not a fully-functional Unix file system.  Please choose a different file system, such as ext2.

Is there a way around this?  Since Linux natively supports FAT32, is there any reason that the root partition cannot be FAT32?

Thanks in advance!

---

### Post by oilchangeguy on 2007-06-29
quote "Is there a way around this?" no. 7.04 supports fat 32, as far as being able to read and write to it. but not to be installed on it.

---

### Post by chamberlain2006 on 2007-06-29
Is there any reason why you want/need fat32, anyway?

---

### Post by Yoooder on 2007-06-29
> **tap52384 said:**
> To those who can help:

Without the hate that comes against all things Microsoft, I was wondering if it were possible to install Ubuntu to a FAT32 partition as the root file system.  While attempting to install Ubuntu 7.04, I tried to specify FAT32 as the file system for the root file system (mount point "/") but then I received an error message:

Invalid file system for this mount point

The file system type fat32 cannot be mounted on /, because it is not a fully-functional Unix file system.  Please choose a different file system, such as ext2.

Is there a way around this?  Since Linux natively supports FAT32, is there any reason that the root partition cannot be FAT32?

Thanks in advance!

FAT does not support any kind of permissions, it is an old and very poor filesystem.  While it is compatible with many OS's, it is too riddled with shortcomings and problems to be considered as a filesystem for an OS anymore.  The only halfway decent application of FAT anymore is on USB Thumb Drives.

If you want Linux on FAT so you can work with your files from Windows, use Ext2 or ReiserFs.  There are drivers/applications available for Windows to access both types of filesystems--and both are far far superior to FAT.

---

### Post by tap52384 on 2007-07-03
The reason for this post was that I was going to attempt to use ImageX, an imaging tool that Microsoft has released that is similar to Norton Ghost to backup my entire Ubuntu operating system into a single file that can retain all of the program settings and everything into a single *.wim file.  But since it cannot be done, I thank you all for your time and answers.

---

