---
title: "Uninstalled Ubuntu, problems with Grub"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Bios___ on 2006-06-17
As the name suggests.

Basically, I have 2 physical Hard Drives, one of which has Xp Pro on it, I was reffered to Ubuntu, so i installed that on the second drive.

Tested ubuntu, thought well of it, and am deciding to put it on a seperate machine as having to choose which OS to load each time can be a pain.

I have removed Ubuntu from my second drive via a format, and now I get a Grub error at startup and it doesnt load Xp at all.

I dont have an Xp Recovery Disc, I have attempted to use the FDISK/MBR commands and they haven't gone too well for me. I caught glimpse of a post explaining that there is a way to remove the Grub loader using the Ubuntu Live CD's, but I lost it and feel like a plank.

Any and all help would be greatly appreciated.

Thank you.

Also I apologise if this post is in the wrong section. Sorry.

---

### Post by catlett on 2006-06-17
When you erased Ubuntu, you erased Grub. Only stage1 of grub is on your mbr. Stage1.5, stage2 and the menu etc are in your grub folder on your Ubuntu partition. So erasing Ubuntu erased grub's folder. That is why the error. Stage1 is activating and searching for Syage1.5 but it can't find it which results in the error.
The best thing for you is to use FIXMBR but that command can only be given when you are in windows recovery mode. It can't be given in any other way. Do you have your computer recovery disks?
Do you have access to another computer? You can download a 3rd party recovery disk like Barts PE [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/) and get a recovery console.

There is another way that is a bit long but if you have no other option. First you need the Dapper ALTERNATE INSTALL CD or Breezy (ubuntu 5.10) install cd. These versions have the text mode for installling. Run the install again. When it gets to the part about grub it will ask you if you want to install grub to the mbr. Say NO. The next screen will ask where you want to put it. Choose the floppy disc (enter /dev/fd0 or hd0) This willl put grub on the floppy instead of ubuntu's partition.
When you start your computer make sure the floppy is in the drive. The computer will boot to the floppy first and it will bring up grub. You can then choose windows.
Now you can erase Ubuntu. The floppy will get you into windows. Use that until you can get a recovery disk. The easiest way is to go online to a bittorrent site. Download an XP install disc. Use that to get to the recovery consol

P.S. Now that I think of it you can download an XP install disk with bittorrent and run fixmbr instead of the Ubuntu install/grub floppy. (if your not use to torrents, go to "The Pirate's Bay" for a good torrent site. Use "Utorrent" for a bittorrent application. It is easy on resources and simple to use)

---

### Post by Bios___ on 2006-06-19
Thank you, sorry I took ages to Re-Post, Thank you.

It worked, fortunatley I had a second computer and found the discs for it, and used the MBR command, it worked a treat. Thank you!

Thanks Catlett. Your a star :D

---

