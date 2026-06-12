---
title: "Windows can't find HardDrive"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Mugmoor on 2007-11-15
I recently installed Ubuntu over my windows on my laptop. I want to setup a Dual boot between the two, but I've been told it is thousands of times easier if I do it through XP. I have my disc for it, so I put it in and reboot. It loads up, starts loading up drivers, then then I'm prompted to start installation, it tells me that XP cannot find my hard disk.

I know it's there, as Ubuntu uses it, so I figure Ubuntu did something that makes Windows unable to find it. How do I fix this?

---

### Post by steve-shinn on 2007-11-15
Is the laptop using a sata hard drive ? if so, you will most likely need to install the appropriate sata drivers during the windows install process.

---

### Post by steve-shinn on 2007-11-15
Installing Windows XP

Serial-ATA
If you are installing to a Serial-ATA Hard Disk then you may need a floppy disk containing the appropriate Serial-ATA drivers for your motherboard.

Quality motherboard manufacturers will supply a floppy disk with the motherboard for this purpose but, in some cases, it will be necessary to create a Serial-ATA driver disk using the CD that is packaged with the motherboard, or even download the drivers from the manufacturer's web site.

The procedure for installing Windows XP onto a new PC is as follows:

Switch on the PC and put the Windows XP CD into the CD-ROM. Press the reset button on the PC and allow it to boot.

The PC should boot to the CD-ROM, if not check your motherboard manual to enable 'Boot to CD-ROM' in its BIOS settings.

Serial-ATA
If you are installing to a Serial-ATA hard disk then keep an eye out for the message (It only appears very briefly):
Press F6 if you need to install a third party SCSI or RAID driver... Tap the [F6] key a few times. The installation will continue, but will stop in a few moments to give you the opportunity to insert a floppy disk with the Serial-ATA drivers on.

After a few seconds a blue Windows Setup screen will appear.

The system will load some basic files to enable it to begin the install

At the Welcome to Setup screen, press ENTER to continue.

The system will check the HDD to determine if / how it is configured

Serial-ATA
If you are installing to a Serial-ATA Hard Disk then Windows will require the Serial-ATA drivers at this point. A message will appear as follows:
Setup could not determine the type of one or more mass storage devices installed in your system, or you have chosen to manually specify an adapter...

Insert your Serial-ATA drivers floppy disk and press [S]. If a list of drivers appears, select the correct driver (the motherboard manual should help you with this choice.) Windows XP should load the appropriate driver and continue to install.

At the Windows XP license agreement screen, read the agreement and press the F8 key to continue.

---

### Post by Jerry N on 2007-11-15
When you installed Ubuntu, the hard drive was probably reformatted to one of the Linux formats (ext3, Reiser, etc).  I think it is unlikely that a Windows install disk will ever recognize a Linux format although you can buy drivers that allow Windows to read and write to Linux disks.  If during the Ubuntu install you partitioned part of your disk as Fat32 or NTFS, then ignore my first two sentences.

Jerry

---

### Post by KOTAPAKA on 2007-11-15
Load up partition magic if you have it and format a part of you hard drive as NTFS and it should be OK. Format at least 10GB so that you  wont have problems with Windows not having enough space.

---

### Post by shad0w_walker on 2007-11-15
The problem is most likely a lack of SATA drivers. The Windows installer will detect a harddrive with ext3 partitions just fine, it just lists the partitions as unknown types.

---

### Post by arashiko28 on 2007-11-15
Don't do that of installing through XP, wy don't you simply make the partition, insert the CD, reboot and follow the instructions, all you have to do is choose manual for disk partition, /sda1 will be your windows partition, for the rest, choose the size of your ram and make a partition of that size make sure to make it SWAP and the other part ext3 writing / to set the mounting point. It'll go smoothly after that. I had to do a double boot too and windows do not recognize my linux partition, it doesn't even know it exists, so i think it's normal. However, I have a free access to the windows partition as sda1 on my desktop, also on computer. I can go in and retreat any file I need.

PS: I told you how to do it, because I think it's easier for new users, no one told me, and had to bang my head with a tube a couple of times:), if you already know, better.

---

### Post by steve-shinn on 2007-11-15
"windows do not recognize my linux partition, it doesn't even know it exists, so i think it's normal"

It will if you install ext2 IFS for windows :-http://www.fs-driver.org/faq.html
:)

---

### Post by jacobsn on 2008-01-03
I will first say thank to the wise meen inside this forum, because i have the same problem..:)

But(there always a but), when i use my sata driver and all sems to get right i get this bug when im installing windows.

**Setup cannot copy the file: nvraid.sys**

i tryed to just say skip the file, but then windows dosn't start Right. 

Hope you can help me, and that my english dosn't is to bad..:confused:

STOP HELPING THE I HAVE FOUND THE BUG.

i installed windows xp tiny.. when i installed windows proffessionel the problem dissapered.. :D

---

