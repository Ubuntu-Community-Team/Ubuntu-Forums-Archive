---
title: "Dual boot with XP - how do I create the partitions?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by GoodOrEvil on 2007-10-05
Greetings all. I'm going to give ubuntu a shot but going to have a dual boot with XP for the software/peripherals that are Windows only and for my technophobe parents and/or guardians (circle one). I've read through a few things and some say I need to defrag the harddrive, uninstall XP and then reinstall it and create the partitions during the install. Others say that ubuntu can create the partitions during the installation process. I currently have one internal harddrive that's roughly 320gb in size and has 40gb of space taken up. Anyone here able to point me in the right direction?

---

### Post by overdrank on 2007-10-05
> **GoodOrEvil said:**
> Greetings all. I'm going to give ubuntu a shot but going to have a dual boot with XP for the software/peripherals that are Windows only and for my technophobe parents and/or guardians (circle one). I've read through a few things and some say I need to defrag the harddrive, uninstall XP and then reinstall it and create the partitions during the install. Others say that ubuntu can create the partitions during the installation process. I currently have one internal harddrive that's roughly 320gb in size and has 40gb of space taken up. Anyone here able to point me in the right direction?

Hi and welcome,  yes Ubuntu can resize the windows partition during the installation. Yes you need to defrag windows before installation. This link will hopefully help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Goos luck!

---

### Post by linuxforrealpeople on 2007-10-05
I have gone through this process fairly painlessly. Start with this excellent article,
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

Good Luck.

---

### Post by GoodOrEvil on 2007-10-05
Thanks for the help and quick reply.

---

### Post by darren1270 on 2007-10-05
I know everyone else told you to defrag.... I just gotta say do it more than once... three times maybe... you want to try and move all the data to the front of the drive.

Good Luck
Darren

---

### Post by GoodOrEvil on 2007-10-05
Okay, from what I gather I'll need 4 partitions - one for ubuntu, one for XP, one shared and one that's twice the size of my RAM. Would I make these during the ubuntu install?

---

### Post by Faud on 2007-10-05
Just remember XP needs to be /hda1

---

### Post by overdrank on 2007-10-05
[QUOTE=GoodOrEvil;3479114]Okay, from what I gather I'll need 4 partitions - one for ubuntu, one for XP, one shared and one that's twice the size of my RAM. Would I make these during the ubuntu install?[/QU

Yes you will need to create these partition during the install. But be sure to _**BACK UP **_your data. Also I noticed you have a 320 gb drive and I would recommend that if you want in the future to have more partitions on that drive ( you can only have four partitions to a drive) to create one as a extended partition and that way you can create addition partition in the future. Good luck!

---

### Post by GoodOrEvil on 2007-10-05
> **overdrank said:**
> [QUOTE=GoodOrEvil;3479114]Okay, from what I gather I'll need 4 partitions - one for ubuntu, one for XP, one shared and one that's twice the size of my RAM. Would I make these during the ubuntu install?

Yes you will need to create these partition during the install. But be sure to _**BACK UP **_your data. Also I noticed you have a 320 gb drive and I would recommend that if you want in the future to have more partitions on that drive ( you can only have four partitions to a drive) to create one as a extended partition and that way you can create addition partition in the future. Good luck![/QUOTE]

Extended partition? Pretty newby at this stuff, sorry.

---

### Post by the_darkside_986 on 2007-10-05
I think you must have a tool like the gparted liveCD in order to make Extended partitions. I cannot figure out how to make them from the Ubuntu install CD. I would like to see future Ubuntu releases actually have a decent partition tool and a ntfs resizer that works without destroying the data.

Anyway, you can use gparted to allocate free space and create a new partition of type "extended" and with the ext3 filesystem. Then you can make partitions inside of that partition. For example, you might make a partition that is mounted at "/" and another partition that is bigger, mounted at "/home" for your personal files.

But I do not recommend using gparted or the Ubuntu installer for resizing the NTFS (windows) drive, but if you are daring, then do as others have said and absolutely back up all your important data.  

If you have a Windows install CD you could perhaps wipe everything and then use gparted to create a smaller NTFS partition, and also use it to make the extended partition for Ubuntu, and then install Windows on to the NTFS partition you made, and then install Ubuntu on a partition inside of the extended partition. Windows has a tendency to want to use the whole drive so it is best to make its NTFS partition from another tool and select that partition during the Windows install.

If you do not have a Windows install CD for whatever reason then do not count on Windows continuing to exist in a functional state. This is a warning from personal experience.

This is the gparted live CD I use: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by GoodOrEvil on 2007-10-05
Alright, think I've got this right.

1) Back everything up.
2) Download ubuntu and burn it as an iso to a disc
3) Defrag multiple times
4) Put in cd and reboot
5) Select install
6) Answer the questions
7) Select manual for partitioning
8.) /hda1(ntfs) should be Windows, swap should be double the size of my ram, one for ubuntu (ext3 I think) and one for shared (fat32?)
9) Finish off the Who Are You questions
10) Check summary and install
11) Sit back for a bit
12) Reboot and remove CD
13) ???
14) Profit!

That sound about right? also, what type should the shared and ubuntu partitions be.

Finally, [this screenshot](http://img509.imageshack.us/my.php?image=feistydual17iv6.png) makes it sound like I'll need to reinstall Windows - will I? I'd rather not cause it could cause a bit of trouble with my OEM disc.

---

### Post by Niniel on 2007-10-05
The live CD partitioning tool is perfectly capable of resizing NTFS without causing problems, at least it worked without a hitch for me. 

If you want to defrag in order to consolidate your files, don't use the built-in defragger of XP because that just does that - defrag files. It does not consolidate them into one block. Use something else, such as DirMS (last time I checked it was free for home use).

---

### Post by GoodOrEvil on 2007-10-05
Alright, thanks. What type should the different partitions be?

---

### Post by Niniel on 2007-10-05
At 320 GB space is not really an issue for you, but if you have a lot of RAM, I don't think the Swap file has to twice as large. 
Linux can boot from logical partitions (unlike Win, which needs a primary partition), so go ahead and create all new partitions as logical partitions. 
You won't have to reinstall as long as all you do to the NTFS (Win) partition is resize it.

---

