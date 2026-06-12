---
title: "Change desktop name of mounted partition?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-06-04
In a dual boot XP/U-FF setup, I unmounted the Windows partition from the desktop.  

There is large logical FAT32 mounted partition called sda5 showing on the desktop that will hold the data files shared by XP and U-FF.  How can I change it to another name like DATA?  

Exact steps are needed.  I cannot even figure out how to login as root.

---

### Post by coffeecat on 2007-06-05
I was going to point you to [this HOWTO]("http://ubuntuforums.org/showthread.php?t=283131"). Scroll down past the main fstab howto to "How to label" and then a bit more to "FAT Windows Partition" and you'll see how to use mtools. But from the wording of your post I think you might find this daunting.

Instead, since you've got a Windows/Ubuntu dual-boot, use Windows to label the FAT32 partition. Ubuntu will then show the partition label with the icon on the desktop.  In Windows:

 Control Centre > Administrative Tools > Computer Management > Disk Management
 
 Right click on partition, choose properties. Type in new label. Click Apply. Click OK.
 
> **bettyhills said:**
> I cannot even figure out how to login as root.

I presume you're new to Linux. A piece of advice. Never, NEVER, **NEVER** log in as root. You can't in Ubuntu anyway, unless you do a bit of reconfiguration, but you can in other distros. Don't. It's insecure. Perhaps what you mean is that you don't know how to gain root privileges. That's a different matter. Some GUI apps need administrative permissions - particularly those in System > Administration - and will prompt you for your password which will give you temporary root status. Similarly in a terminal in Ubuntu, prefacing a command with 'sudo' will give you temporary root access. Have a look at [this]("https://help.ubuntu.com/community/RootSudo"). It gives some more information.

Oh, and did I say never to log in as root? :wink:

---

### Post by bettyhills on 2007-06-05
Thanks.  The guidance was tremendously helpful.

---

