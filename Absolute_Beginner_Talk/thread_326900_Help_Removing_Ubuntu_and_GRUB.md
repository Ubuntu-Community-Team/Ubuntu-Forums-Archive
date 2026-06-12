---
title: "Help Removing Ubuntu and GRUB"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by trevor1189 on 2006-12-28
I need some help uninstalling ubuntu and GRUB. I have searched the forum and I know there are some methods that involve a windows recovery disk, but my PC didn't come with a recovery disk. Here is my setup: I have Windows XP on the master 40 GB hard drive and Ubunutu and I am assuming GRUB on a second Slave 20 GB drive. Before I installed Ubuntu, I just used the command prompt the reformat the secondary hard drive (which had win2k on it), can I just do the same to remove ubuntu and GRUB? I just wanted to check here before doing that, because I want to make sure after removing GRUB I can still boot my PC. All help is appreciated. 

P.S. I would love to keep Ubuntu on the 2nd HD, but unfortunately my master drive is nearly full and I need more room for my digital media.

---

### Post by dmartinsca on 2006-12-28
To remove Ubuntu, start windows xp, right click on my computer and click manage. In the window that opens, click on disk management. You can format your secondary drive with a filesystem windows understands (NTFS) from here. To remove grub, you'll need to re-write the master boot record of the hard drive with the windows equivalent of grub. If you don't have a windows cd then you'll need a DOS bootdisk that has the fdisk command on it. You can get one for free from [www.bootdisk.com](www.bootdisk.com) or you can make your own by formating a floppy disk in windows as a system disk then finding the fdisk program on your PC and putting it on. Anyways, once you've booted from the floppy, you need to run **fdisk /mbr** to restore a Windows style bootloader.

---

### Post by mikewhatever on 2006-12-28
See here for instructions:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by bluemanfu on 2006-12-28
I have no clue what the heck "MBR" is,  I only have Ubuntu on my computer.  I am computer illiterite.  All I want to do is remove it and move on with my life :)

---

### Post by mikewhatever on 2006-12-28
MBR=Master Boot Record. You will know, if you take some time and read a little. If you don't have any other operating system on your PC, you can just boot with Ubuntu installation CD and delete Ubuntu partition. Before you do that, how are you going to use the computer? Have I wrongly asumed you had Windows too?

---

### Post by mikewhatever on 2006-12-28
Just reread your first post. You do have Windows!!!??? So what do you mean by 'only Ubuntu'?

---

### Post by dmartinsca on 2006-12-28
bluemanfu, If you only have ubuntu installed, then to uninstall it you simply install something else over top. So if you want to use Windows, insert a windows cd and restart your computer (you may need to change the boot order in the BIOS -- something you may have been required to do to install ubuntu in the first place). When it comes to the screen about where to install windows you'll need to choose to delete the ubuntu partition and format it for use with windows (of course it won't say this exactly since Windows has no clue what Ubuntu is). Once this step is done, ubuntu will effectively be "uninstalled"

---

### Post by dmartinsca on 2006-12-28
> **mikewhatever said:**
> Just reread your first post. You do have Windows!!!??? So what do you mean by 'only Ubuntu'?

I don't think bluemanfu is the original poster.

---

### Post by mikewhatever on 2006-12-28
You're right, it was Trevor1189. Bluemanfu is someone else...?

---

