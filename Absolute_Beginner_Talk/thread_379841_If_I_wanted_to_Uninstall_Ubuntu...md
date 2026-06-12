---
title: "If I wanted to Uninstall Ubuntu.."
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2007-03-08
Hello

I am considering installing the latest build of Ubuntu (6.10) and I am wondering if for whatever reason Linux doesn't work out for me, will it be easy to uninstall as easy as it was to install? Also, is there any very easy to understand guides to help me learn how to uninstall all of Ubuntu successfully if I choose to do so? Thanks in advance.

---

### Post by hanexar on 2007-03-08
You just have to format the hard drive where it is installed.

---

### Post by halitech on 2007-03-09
couple of options, boot from a floppy (if present) with a boot image from bootdisk.com and fdisk the drive to remove all partitions and then recreate them, boot from gparted livecd and do the same thing, run a powerful magnet over the drive (may or may not work after doing this though so please don't actually do it :D )

---

### Post by dhughes on 2007-03-09
If you dual boot with Windows you'll have to repair the master boot record (MBR) since GRUB would have replaced that, it's not too hard in a Command Prompt FIXMBR I think?

 Gparted is a great tool to have no matter what OS you use, keep the Live CD handy to resize partitions.

---

### Post by Kateikyoushi on 2007-03-09
First fix the MBR to boot windows by default.

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

Then use the disk manager in system tools to remove the ubuntu partitions from the hard disk and create ones which windows can use.

For a longer guide look here. [LINK]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by bot42 on 2007-03-09
To dswhite: Don't bother with 6.10, its not the most stable version, you should try waiting for 7.04 which is coming out next month and is currently in beta. by the way i upgraded from 6.06 to 6.10 (edgy), so dapper is the best version thats currently available although 7.04 seems like it could take that place.

To the others: I was gonna set up a ubuntu/ windows 98 SE (so i can have a LAN network for older games without registering another copy of XP) system by having one harddrive for each operating system. Problem is i'm going to format one of my ubuntu drives which be used store windows 98 SE and i do not know how to format using fdisk. Could someone please give me the exact instructions?

---

