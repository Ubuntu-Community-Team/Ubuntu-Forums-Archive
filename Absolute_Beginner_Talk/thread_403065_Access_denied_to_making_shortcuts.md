---
title: "Access denied to making shortcuts"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ravenus on 2007-04-06
Hi, It's been 4-5days since I installed Ubuntu 6.10 as a dual-boot on my WinXP machine. Apart from my NTFS partitions and Linux install partitions, I have a FAT32 partition on which I am storing files to be used in Linux as well as installing some games.

When I try to make a shortcut in Ubuntu for any folder/file on this partition, it gives me an access denied msg. When I go to the permissions tab, it lists the owner of the folder/partition as root and tells me that I am not the owner. I have set up Ubuntu as a single-user thing and I am able to do everything in Synaptic using my admin password. But here there is no option for me to enter a password.

Please advise.

---

### Post by Nekiruhs on 2007-04-06
I know the exact solution to your problem.  Open a terminal (Applications > Accessories > Terminal) and type in "gksudo nautilus" (without the quotes of course).  This will request a password, just use the one you use to login.  Dont worry if you get some error messages in the terminal just hang on, itl take a few seconds.  When a window comes up looking like the main file explorer, you have root permissions for the filesystem. You can make an easy access launcher by right clicking the desktop and selecting Create Launcher.  Then type into the command box "gksudo nautilus" (again, no quotes) and choose a Name and an Icon for it.  

I hope this helps!

---

### Post by lukew on 2007-04-06
> **ravenus said:**
> Hi, It's been 4-5days since I installed Ubuntu 6.10 as a dual-boot on my WinXP machine. Apart from my NTFS partitions and Linux install partitions, I have a FAT32 partition on which I am storing files to be used in Linux as well as installing some games.

When I try to make a shortcut in Ubuntu for any folder/file on this partition, it gives me an access denied msg. When I go to the permissions tab, it lists the owner of the folder/partition as root and tells me that I am not the owner. I have set up Ubuntu as a single-user thing and I am able to do everything in Synaptic using my admin password. But here there is no option for me to enter a password.

Please advise.

That sounds to me like you need to run fsck. You have some inconsistency in your hd and it is turning it readonly. Linux mounting vfat does not have file permissions.

Luke

---

