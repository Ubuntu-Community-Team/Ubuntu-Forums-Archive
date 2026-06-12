---
title: "What is the root filesystem?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Wotcher on 2007-05-28
I need help understanding this.

Just to orient you: I have one hard drive, and on it I have three partitions: #1 is Windows XP, #2 is Dapper Drake, and #3 is the swap file.

I'm attempting to perform a clean install on the #2 partition so that I can upgrade to Feisty Fawn. I'm using the alternative CD to do so. When I get to the partition part, I am told that I need to indication a root filesystem. I have been told in another thread that this means that I need to label a partition as "/"

Now, the problem that I am having is that I am not sure which partition I am supposed to label in this manner. Is it #1 (the Windows XP partition), or #2 which will house Feisty Fawn.

Another concern: I want the computer to ask me which OS to boot in when I turn on my system. This is the method that I have it on right now. Will selecting a root filesystem have any affect on this method?

If someone could explain to me what the root filesystem is and why it is important, I think I will understand much better. Thank you for your time. :p

---

### Post by starcraft.man on 2007-05-28
Ok, I think a bit of reading material will get this answered.

[This]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") explains how the file system is set up.
[This]("http://www.psychocats.net/ubuntu/installing") explains how to install and partition using the live cd.
[This]("http://users.bigpond.net.au/hermanzone/p2.htm") explains how to do a dual boot with the alternate CD (even if you don't have alternate, its a good read to understand what your doing).
[This]("http://www.psychocats.net/ubuntu/partitioning") talks about partitions, and how you should plan them. 

Just a bit of reading material to understand how the installer and other things work in future. It's good to know these things, partitions in particular apply to any OS.

The simple answer to your question is when you get the partitioner, remount your old dapper partition as the root (/). This will overwrite it (make sure it says it will format before installing) and install feisty in its place. Oh and the XP partition should simply be mounted as an hda/sda drive so you can browse it while your booted in Ubuntu. Then just let it remount the swap as well. Grub will take care of the booting and give you both options.

Have a read through the links, then you should be all set. :D.

---

### Post by jeblinux on 2007-05-28
The root file system is the main file system for your Ubuntu install. You can change to the root diretory on the root file system by typing

cd /

at a command prompt.

This file system is consequently called '/'. Make partition #2 your root file system to overwrite the old Dapper Drake installation with Fiesty Fawn.

Grub is the boot loader that you see at startup that allows you to select an operating system. It will not configure grub any different when you choose #2 as the location for the root file system. If you want to customize Grub look for documentation on it. The configuration file for it is usually at

/boot/grub/menu.lst

See. There is that root file system again. The path  to the file above starts with '/'. 'boot' is a directory on the root filesystem.

---

### Post by Wotcher on 2007-05-28
So, when you indicate the root filesystem as "/" it means that this is the place where Ubuntu will be installed to?

> **starcraft.man said:**
> Ok, I think a bit of reading material will get this answered.

[This]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") explains how the file system is set up.
[This]("http://www.psychocats.net/ubuntu/installing") explains how to install and partition using the live cd.
[This]("http://users.bigpond.net.au/hermanzone/p2.htm") explains how to do a dual boot with the alternate CD (even if you don't have alternate, its a good read to understand what your doing).
[This]("http://www.psychocats.net/ubuntu/partitioning") talks about partitions, and how you should plan them. 

Just a bit of reading material to understand how the installer and other things work in future. It's good to know these things, partitions in particular apply to any OS.

The simple answer to your question is when you get the partitioner, remount your old dapper partition as the root (/). This will overwrite it (make sure it says it will format before installing) and install feisty in its place. Oh and the XP partition should simply be mounted as an hda/sda drive so you can browse it while your booted in Ubuntu. Then just let it remount the swap as well. Grub will take care of the booting and give you both options.

Have a read through the links, then you should be all set. :D.

---

### Post by Wotcher on 2007-05-28
Thanks jeblinux! Now I understand.

Thanks again for quelling my concerns.

> **jeblinux said:**
> The root file system is the main file system for your Ubuntu install. You can change to the root diretory on the root file system by typing

cd /

at a command prompt.

This file system is consequently called '/'. Make partition #2 your root file system to overwrite the old Dapper Drake installation with Fiesty Fawn.

Grub is the boot loader that you see at startup that allows you to select an operating system. It will not configure grub any different when you choose #2 as the location for the root file system. If you want to customize Grub look for documentation on it. The configuration file for it is usually at

/boot/grub/menu.lst

See. There is that root file system again. The path  to the file above starts with '/'. 'boot' is a directory on the root filesystem.

---

### Post by starcraft.man on 2007-05-28
> **Wotcher said:**
> So, when you indicate the root filesystem as "/" it means that this is the place where Ubuntu will be installed to?

Yup basically, all your systems files are contained in the root. You can of course create seperate partitions for directories like home, boot or usr folder. It's not really needed though. The only other thing most installs have as a partition is swap-file. That is the equivalent of paging file used in windows, usually a GB of that is enough, you already have one so continue to use it. Its only real purpose is scratch surface on your HD if it runs out of ram.

For more info about what all the directories do, read the wiki article, my first link.

---

### Post by Wotcher on 2007-05-28
Ok, thank you.

You were all very helpful, I'm running the installation right now on my other computer. Hope for the best! :KS

> **starcraft.man said:**
> Yup basically, all your systems files are contained in the root. You can of course create seperate partitions for directories like home, boot or usr folder. It's not really needed though. The only other thing most installs have as a partition is swap-file. That is the equivalent of paging file used in windows, usually a GB of that is enough, you already have one so continue to use it. Its only real purpose is scratch surface on your HD if it runs out of ram.

For more info about what all the directories do, read the wiki article, my first link.

---

