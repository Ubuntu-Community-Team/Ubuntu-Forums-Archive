---
title: "Please help me!"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by icett on 2007-08-01
I have a Pentium 4 PC with 500 mb Ram and 256mb nvidia graphics card, one CD rom, one CD writer, one DVD rom, 200 GB harddisk. From the vendor from whom I purchased the system, I got the harddisk partitioned into 3 equal sections. One for Windows 98 SE, one for Windows XP Pro and one for their extra softwares like games etc. From long I wished to migrate to Linux and I downloaded the Ubuntu CD and successfully burnt it. Today I installed Ubuntu but during installation I could not understand into which partitiion of my harddrive I am installing it. After its installation, my Windows XP Pro stopped working with the message that the root file is missing. Fortunately my Windows 98 SE survived and I tried to look into my harddisk partitions. I could not find Ubuntu Linux files anywhere. Also the headings of one of the three partitions has changed like instead of  "Local Disk (D:)" its only "D" now while "Local Disk (C:) and Local Disk (E:) are still there. Also my Ubuntu installation seems to include the Windows XP softwares also. Please let me know the way as to how to install Ubuntu without disturbing my other OSs. How can I uninstall Ubuntu now that I can not see its contents and where it is? Also I wish to use my Ubuntu OS completely seperate from Windows and not using Windows software instead it should use pure Linux software only. Please inform me what could I do now to restore my Windows XP, Restore the heading "Local Disk (D:), uninstall and reinstall Ubuntu completely seperately. Please guide me! One thing, Ubuntu Linux is very stable. :)

---

### Post by tchoklat on 2007-08-01
To uninstall Ubuntu just delete the partition it is on.

You can use the Live CD to load GPartEd to do this. The partition with an Ext2 or Ext 3 file system will be the Ubuntu partition. The others will be FAT32 or NTFS. The Live CD install should automatically install Ubuntu for you without a hitch.

Remember Linux and WIndoze 'name' disks and partitions differently, C:/ and hd1 etc.

when you installed it a new bootloader should have been created for you listing your operating systems, did this occur?

---

### Post by icett on 2007-08-01
> **tchoklat said:**
> To uninstall Ubuntu just delete the partition it is on.

You can use the Live CD to load GPartEd to do this. The partition with an Ext2 or Ext 3 file system will be the Ubuntu partition. The others will be FAT32 or NTFS. The Live CD install should automatically install Ubuntu for you without a hitch.

Remember Linux and WIndoze 'name' disks and partitions differently, C:/ and hd1 etc.

when you installed it a new bootloader should have been created for you listing your operating systems, did this occur?




Thanks for your guidance. Pardon me if I ask some baseless questions or talk baseless, for I am really an absolute beginner even to the PC technically so I hope you would bear with me. Yes a Grub bootloader was created listing my OSs. Could you please guide me as to how I delete and recreate the partition I suppose has got some change that is "D" and recreate it? Also my PC does not boot from the Ubuntu disk when I restart it. I have to constantly push F10 to get it. Could you guide me as to how I could install Ubuntu using the Live CD? Thanks again for your precious time. :)

---

### Post by logos34 on 2007-08-01
To give us a better picture of what's going on here, boot from the ubuntu livecd, mount your root partition (if you can), open a terminal and type these commands:
[B]
sudo fdisk -l[/B] (lowercase L)
[B]
cat /boot/grub/menu.lst[/B]

Post the output.

I don't know what error message you're getting in the grub menu screen when you try to boot ubuntu, but maybe the path is wrong.  Also, ubuntu would not have installed on a windows partition--you can't have two OS's coexisting on the same one.  I'm not sure if you used the alternate cd or live cd to install, but either way it looks like the debian installer formatted and overwrote XP partition with linux. And windows can't see any linux partitions--you need a special driver for that (ext2fs/fs-driver)

---

### Post by icett on 2007-08-01
> **logos34 said:**
> To give us a better picture of what's going on here, boot from the ubuntu livecd, mount your root partition (if you can), open a terminal and type these commands:
[B]
sudo fdisk -l[/B] (lowercase L)
[B]
cat /boot/grub/menu.lst[/B]

Post the output.

I don't know what error message you're getting in the grub menu screen when you try to boot ubuntu, but maybe the path is wrong.  Also, ubuntu would not have installed on a windows partition--you can't have two OS's coexisting on the same one.  I'm not sure if you used the alternate cd or live cd to install, but either way it looks like the debian installer formatted and overwrote XP partition with linux. And windows can't see any linux partitions--you need a special driver for that (ext2fs/fs-driver)



Thanks for your info. Just before I read your advise I went into my "C" drive which has Windows 98 SE and I formatted the "D" drive which had Windows XP Pro and also "E" drive. This to ensure that I have removed Ubuntu installation but to my surprise when I restarted the PC the Grub menu again came up to choose the operating system and I chose Ubuntu and Ubuntu started successfully. For your information I did not install ubuntu from my Live CD but I restarted my PC to reboot constantly pressing F10 key to bring up the installation option and installed it from there. I hope that you might have understood the picture now and assume that it may not be necessary to boot from the ubuntu live cd as you advised. But if its necessary please let me know and in case you have understood the matter please guide me what could I do now. With my regards and appreciation for your helping hand. :)

---

### Post by logos34 on 2007-08-01
> I went into my "C" drive which has Windows 98 SE and I formatted the "D" drive which had Windows XP Pro and also "E" drive. This to ensure that I have removed Ubuntu installation but to my surprise when I restarted the PC the Grub menu again came up to choose the operating system and I chose Ubuntu and Ubuntu started successfully. For your information I did not install ubuntu from my Live CD but I restarted my PC to reboot constantly pressing F10 key to bring up the installation option and installed it from there. I hope that you might have understood the picture now

I have to confess that I don't...When you format a drive/partition, you basically erase everything and lay down a clean filesystem, NTFS, ext3, fat32, etc.  How ubuntu came back and now boots ok is a mystery to me.  It would seem XP is gone.  You'll have to reinstall it to another partition.  Not sure if it will boot or not since win98 is on the first partition.  Post those commands from above.

---

### Post by icett on 2007-08-01
> **logos34 said:**
> I have to confess that I don't...When you format a drive/partition, you basically erase everything and lay down a clean filesystem, NTFS, ext3, fat32, etc.  How ubuntu came back and now boots ok is a mystery to me.  It would seem XP is gone.  You'll have to reinstall it to another partition.  Not sure if it will boot or not since win98 is on the first partition.  Post those commands from above.




logos,


I tried my best to get the commands as you mentioned but I am unable to accomplish this.:( Now what I think is practicable is that I format my complete hard drive including linux section which is unvisible to windows and recreate three equal partitions of the hard disk, one for Windows 98 se, one for Windows XP Pro and one for Ubuntu Linux. But I don't have sufficient technical knowledge as well as the knowledge of commands etc. to do it my self. I humbly request you therefore to please guide me step by step to do all that. I yearn to see my PC with all these OSs cleanly installed since I have now got a taste of the stablility and smoothness of Fiesty Fawn I can not think of my PC without Linux anymore. Please guide me may be some day I begin to contribute to this great OS.:)

---

### Post by Sayers on 2007-08-01
I've always had problems with Dual-Booting because Windows plainly doesn't like it. Thus I suggest creating your own partiton table for ubuntu or buy a 40 gb hard drive or, kill windows. However the easiest option would be to learn how to partion Ubuntu without interfearing the others.

---

