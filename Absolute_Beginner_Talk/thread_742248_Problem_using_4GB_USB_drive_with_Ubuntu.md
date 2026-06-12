---
title: "Problem using 4GB USB drive with Ubuntu"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by trnuptheradio on 2008-04-01
Hi,

I need help with a problem accessing a Matsunichi 4gb drive on a Linux Ubuntu system...

I can get to it on a windows machine, and it has worked in the past on my Linux machine - when I try to copy a file to it under Linux, I get the message:

Error while copying to "/media/disk".

You do not have permissions to write to this folder.

There is a desktop.ini file on the drive - here's the contents...

[.ShellClassInfo]
InfoTip=@Shell32.dll,-12689
IconFile=%SystemRoot%system32SHELL32.dll
IconIndex=-237

The drive worked on Linux just fine - the problem started after it was used on a windows pc

I have no background with Linux, absolute beginner, any help is appreciated,

Thanks,

Chuck

---

### Post by stchman on 2008-04-01
> **trnuptheradio said:**
> Hi,

I need help with a problem accessing a Matsunichi 4gb drive on a Linux Ubuntu system...

I can get to it on a windows machine, and it has worked in the past on my Linux machine - when I try to copy a file to it under Linux, I get the message:

Error while copying to "/media/disk".

You do not have permissions to write to this folder.

There is a desktop.ini file on the drive - here's the contents...

[.ShellClassInfo]
InfoTip=@Shell32.dll,-12689
IconFile=%SystemRoot%system32SHELL32.dll
IconIndex=-237

The drive worked on Linux just fine - the problem started after it was used on a windows pc

I have no background with Linux, absolute beginner, any help is appreciated,

Thanks,

Chuck

If there is nothing on the drive use gparted to delete the partition and create a new FAT32 partition.

---

### Post by billgoldberg on 2008-04-01
Press alt+f2 and type "gksudo nautilus".

If you copy files then you should have permission.

(this will open the file manager with root access)

---

