---
title: "Dual boot"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Spelaeode on 2007-09-09
I intend installing 7.04 Feisty Fawn. Having taken a first look at the installation process, I am not at all sure about the partitioning and boot loader.

I have Windows XP as my current OS, I wish to be able to choose from a boot loader which OS to run. Does Ubuntu write a dual boot loader automatically. In a previous Mandrake installation, it automatically wrote LILO as the boot loader.

Re- partitioning: I am uncertain about this too. I don't want to make any unrecoverable mistakes. I could use 50% of my current boot SATA drive or use some of my second SATA drive; is there a preferred method?

I would appreciate some experienced guidance guys.

Thanks:confused:

---

### Post by Steve1961 on 2007-09-09
> **Spelaeode said:**
> I intend installing 7.04 Feisty Fawn. Having taken a first look at the installation process, I am not at all sure about the partitioning and boot loader.

I have Windows XP as my current OS, I wish to be able to choose from a boot loader which OS to run. Does Ubuntu write a dual boot loader automatically. In a previous Mandrake installation, it automatically wrote LILO as the boot loader.

Re- partitioning: I am uncertain about this too. I don't want to make any unrecoverable mistakes. I could use 50% of my current boot SATA drive or use some of my second SATA drive; is there a preferred method?

I would appreciate some experienced guidance guys.

Thanks:confused:

First of all, whatever route you take make sure you back up first.  In most cases installation is problem free, but backing up first is always good practice.

As for your other questions, by default Ubuntu will install grub (the bootloader) in the mbr of your primary hard drive.  This will give you the option of booting windows or Ubuntu.  Where you put Ubuntu is up to you.  Personally I install it to a second hard drive, but you can install it it to your main Windows drive if you wish.  If you do this you should first defrag the drive thoroughly.  You can then shrink the widows partition with programmes such as partition magic or Acronis Disk director to make space for Ubuntu.  You then install Ubuntu to the free space and the installer will create the partitions you need automatically.  Alternatively, the installer can shrink your windows partition as part of the installation process.  There isn't a right or wrong way, as both methods work well on the whole.

If you want to install to your second hard drive, if there's already some unpartitioned space there you can install to that, or again shrink any existing partitions to create space.

Either of the above methods really depend on just two steps:

1. Create space for Ubuntu
2. Allow Ubuntu to automatically install to that space and create partitions as needed.

If you're unsure about partitioning this keeps things as simple as possible.  However, you can also create the necessary partitions yourself before installation, although I wouldn't recommend this method if you're unsure about the partitioning process.

Good luck :)

---

### Post by Marc Hoffman on 2007-09-09
I would take a look at this [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")  following these tutorials I have got my laptop dual booting XP and Ubuntu with no headaches.

---

### Post by Spelaeode on 2007-09-09
Thanks Steve. Re- defrag and backups, that is all done. I'll take your advice and install to my second drive. I have Partition magic and had thought of creating a linux partition, however, I was unsure whether Ubuntu would recognise that method; you have allayed my fears!

Many thanks

Phil:)

---

### Post by rolnics on 2007-09-09
I would leave Partition Magic out of this! It caused issues after I installed Ubuntu, can't remember the error message, but it seems quiet common after I do a google on it.

---

### Post by erfahren on 2007-09-09
> **rolnics said:**
> I would leave Partition Magic out of this! It caused issues after I installed Ubuntu, can't remember the error message, but it seems quiet common after I do a google on it.

Yeah, I've read about that (or possibly something similar). [http://www.brunolinux.com/04-The_File_System/Partitioning_Tools.html](http://www.brunolinux.com/04-The_File_System/Partitioning_Tools.html)

He recommends GParted.

There's some good info on using the alternative Ubuntu CD at [hermanzone](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning). I've found it easiier to partition with than the Live CD.

---

### Post by bobpur on 2007-09-09
Gparted can be found at: [www.distrowatch.com](www.distrowatch.com). Also, System Rescue CD. Both can take care of your partitioning needs.

---

### Post by soma4me on 2007-09-09
Spelaeode,

I can see you're very cautious, dual boot can be very interesting.    Please do a search in the forum home page with this string: "dual boot" +WinXP.    You'll get tons of discussion on this topic.

Hope this help.

---

### Post by logos34 on 2007-09-09
Here's another link with a lot of good info:
[Dualboot Two Hard Drives]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by mramsey on 2007-09-09
I prefer to use gparted and the alternate install method with the text based installer. I think it helps you understand what the install process is doing.

---

### Post by Sef on 2007-09-09
Spelaeode:

> I have Partition magic ....

rolnics:

> I would leave Partition Magic out of this!


Partition Magic and GNU/Linux do not always get along.  [GParted]("http://gparted.sourceforge.net") is a better option.

---

