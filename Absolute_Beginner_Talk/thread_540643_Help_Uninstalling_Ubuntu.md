---
title: "Help Uninstalling Ubuntu"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by sherlockmcbride on 2007-09-01
Ok, I installed Ubuntu thinking it would be a great alternative to Windows, and because I'm a big open-source and free software fan (I already use Firefox and Open Office in Windows). However, Ubuntu doesn't like my computer at all. I couldn't get it to work with my wireless network, and my printer doesn't have a supported Linux driver. I don't really have time to get those things to work, so I chose to uninstall Ubuntu. Following instructions on a site that I found using Google (I don't remember the URL right now), I deleted the Ubuntu partition and reformatted it to be an NTFS partition. I was planning on rebooting to my XP Install CD and fix the MBR, however, the only options it gives me when booting to the CD is to "Preform Full System Restore (Destructive)" and "Preform Full System Restore (With Backup)".
I don't want to have to reinstall XP, but when I reboot now it comes to the GRUB thing and it gives me an error and won't boot to XP. So I'm typing this post on another computer. I need help! I just need to know if there is a way to bypass GRUB and get to XP, or if there is another way to restore the MBR (maybe by booting to a USB drive or something?).

Thanks!

Oh, and here are some facts about my comp:

Running (or rather not running at the moment) Windows XP Media Center 2005
Gateway Laptop
512 MB Ram
1.79 GHZ Processor

---

### Post by rsambuca on 2007-09-01
You need the actual XP installation discs, not those annoying restoration cds that you get from the big-box manufacturers.  You can just borrow a friend's installation cd to restore the mbr as you don't need product keys or anything.

---

### Post by overdrank on 2007-09-01
> **sherlockmcbride said:**
> Ok, I installed Ubuntu thinking it would be a great alternative to Windows, and because I'm a big open-source and free software fan (I already use Firefox and Open Office in Windows). However, Ubuntu doesn't like my computer at all. I couldn't get it to work with my wireless network, and my printer doesn't have a supported Linux driver. I don't really have time to get those things to work, so I chose to uninstall Ubuntu. Following instructions on a site that I found using Google (I don't remember the URL right now), I deleted the Ubuntu partition and reformatted it to be an NTFS partition. I was planning on rebooting to my XP Install CD and fix the MBR, however, the only options it gives me when booting to the CD is to "Preform Full System Restore (Destructive)" and "Preform Full System Restore (With Backup)".
I don't want to have to reinstall XP, but when I reboot now it comes to the GRUB thing and it gives me an error and won't boot to XP. So I'm typing this post on another computer. I need help! I just need to know if there is a way to bypass GRUB and get to XP, or if there is another way to restore the MBR (maybe by booting to a USB drive or something?).

Thanks!

Oh, and here are some facts about my comp:

Running (or rather not running at the moment) Windows XP Media Center 2005
Gateway Laptop
512 MB Ram
1.79 GHZ Processor

HI this may help
[http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector](http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector)

---

### Post by southernman on 2007-09-01
I hate to see you give up with only one post on the forum, that one post being this one. tsk tsk.

It isn't for certain, but it is more likely than not that you could have posted a thread here asking for help with your brand of wireless card... and gotten it working.

Oh well! Better luck next time. There will be a next time cause you've been bitten by the Ubuntu Bug! ;)

Back on topic now...

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php")

^^^ That may help if your not privy to a friend with a cd for you to borrow.

---

### Post by ddrichardson on 2007-09-01
If you have access to an actual Windows XP disc:
1.  Boot with Windows XP disc
2.  Select Recovery Console.
3.  Type **fdisk /mbr**
4.  Restart

---

### Post by louieb on 2007-09-01
Don't have a ms install CD no problem. Several methods described here. [Remove/Replace Grub (Dual Boot Site)]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

