---
title: "Dual boot Windows and Ubuntu"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by biggiemokey on 2008-04-16
I am planning to dual boot both Ubuntu and Windows XP from the same hard drive after being a faithful Windows user.  I have no experience with Linux but would like to learn, and Ubuntu looks like the GUI will make it easy.  I have a few questions about the dual boot.

1)  Do I need an anti-virus for Linux?  My windows will be connected to the internet (so will Ubuntu) but I will be running Norton 360 with firewall, etc.  I plan on running both a firewall and anti-virus in Ubuntu, but do you guys think it's necessary?

2)  How many partitions do I need to make?  I would like to configure it so that if I click a .doc file in Windows or Ubuntu it will open up in Open Office in both Ubuntu and Windows.  I do, however, need to have .doc files compatible with Microsoft Word and .ppt files compatible with Microsoft Powerpoint since I work with those at school, and have already had trouble with Open Office Impress.  I know I have to make a partition for Windows XP, and I'll find somewhere else how much space to leave, but how much room should I leave for Ubuntu 8 and future updates?  Can I just partition off Windows and leave the rest of the hard drive for Ubuntu and other files?  I have a 160GB hard drive if that helps.

3)  Is WINE necessary if I have Windows XP?  I have a Zune and plan on using XP for that unless I can use Ubuntu.  I'm sure I'll think of other stuff that won't run on Ubuntu.

Thanks for any help, sorry for the huge post.  And btw I really like the community here, much nicer than Windows users

---

### Post by oilchangeguy on 2008-04-16
> **biggiemokey said:**
> I am planning to dual boot both Ubuntu and Windows XP from the same hard drive after being a faithful Windows user.  I have no experience with Linux but would like to learn, and Ubuntu looks like the GUI will make it easy.  I have a few questions about the dual boot.

1)  Do I need an anti-virus for Linux?  My windows will be connected to the internet (so will Ubuntu) but I will be running Norton 360 with firewall, etc.  I plan on running both a firewall and anti-virus in Ubuntu, but do you guys think it's necessary?

no a/v is needed in the linux world. ubuntu has a built in firewall, iptables.

2)  How many partitions do I need to make?  I would like to configure it so that if I click a .doc file in Windows or Ubuntu it will open up in Open Office in both Ubuntu and Windows.  I do, however, need to have .doc files compatible with Microsoft Word and .ppt files compatible with Microsoft Powerpoint since I work with those at school, and have already had trouble with Open Office Impress.  I know I have to make a partition for Windows XP, and I'll find somewhere else how much space to leave, but how much room should I leave for Ubuntu 8 and future updates?  Can I just partition off Windows and leave the rest of the hard drive for Ubuntu and other files?  I have a 160GB hard drive if that helps.

simply allow ubuntu to set it's own partitions.

3)  Is WINE necessary if I have Windows XP?  I have a Zune and plan on using XP for that unless I can use Ubuntu.  I'm sure I'll think of other stuff that won't run on Ubuntu.

it's a personal preference. i've never used it.

Thanks for any help, sorry for the huge post.  And btw I really like the community here, much nicer than Windows users

read answers between the lines.

---

### Post by Meskarune on 2008-04-16
You cannot have both window's and ubuntu running at the same time in a dual boot. Only one OS's would be running at once. If you wanted both you would have to set up a virtual machine, which is probably too complicated to start with. 

And as for anti-viruse for ubuntu....I actually run one, but I'm also paranoid and travel, so my computer connects to foriegn networks a lot. You really shouldn't have to worry about it so much. But a firewall is good on any system. :)

---

### Post by Harpoon on 2008-04-16
Happy to see you are giving linux a try.  To answer your questions:

1)  Linux does not need an anti-virus program. (You can do a search in the forums to find many posts on why this is true).

3)  If you have a working windows set up, you don't **need** a program like wine, but it can be a time saver.  If, for example, you are doing something in linux that will take some time to complete and find you need or want to run a windows program for some reason, wine will allow you to do that without having to stop your work, reboot, then restart.  That, of course, depends on whether the specific program works well with wine.  (I suggest you check here or the wine website to see about compatability/bugs/etc for specific programs).

2) This is a bit more difficult.  The easiest way is to make a partition to hold your shared files and format it as FAT32 or NTFS.  Both Linud and windows will see it without any issues.  If you store the data in ext2 or ext3, then you can install a program in windows to allow your xp to read the files. Do a search for "Ext2IFS_1_10c.exe." It has worked well.

There are a lot of posts about the best way to partition a drive, and you might want to check some of those before making a decision.  Everyone has different needs and opinions, so there is no one right solution. 

If you need more help with that, post a question here  and we'd be happy to help.

Enjoy the ride!

---

### Post by Kinst on 2008-04-16
There haven't really been any successful linux viruses. Antivirus software just cleans windows viruses that wind up on your computer and sit there.

When dual-booting, you pick between windows and linux every time you turn your computer on. Ubuntu should have no problem reading stuff off your windows partition, and can write to it  after installing an addon. You can also create a small shared partition for them to both read off of.

Wine kicks ***. I run Word, Powerpoint, Excel and Onenote 2003 and 2007, and Photoshop CS2 using it.

---

