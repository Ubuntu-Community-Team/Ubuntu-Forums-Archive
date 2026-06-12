---
title: "Ubuntu/Linux Noob Boot Freeze"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Wizhk on 2007-03-11
Hello, and thank you for your support. I am a Linux noob but not a computer noob. So as I look through the forums for answers to my problems I see a lot of things that I have no clue about. like edgy, bum, etc.. Some of these sound like they may be tools that can help me but im unsure.

** formatted hard drive to Fat32(could go to linux ext2 or ext3 no clue if these are just old or what) **

So the issue is as I boot from the Ubuntu 6.06 CD that I created it takes me to the first boot splash screen I have chosen to check the CD, and to install. No matter what I do it freezes at "mounting Root System Folder" I never get an OK, have to hard boot, CD stops responding, Absolutely Frozen.

I burned a new CD with NERO. Track at once, at 10X (down from 40X) as recommended on another post. I still had the same issues. 

Checked MD5 to the web and all is fine. 

Installing 6.06 x386 iso
Pentium III 500 Mhz.
640 Mb PC-100
17G hard drive

I would really like to check out the world of Ubuntu so any help would be appreciated.

---

### Post by igknighted on 2007-03-11
FAT32 is a windows file system.  It is very outdated and unstable.  Ext2 is an older linux file system, but very stable.  Ext3 is is a newer version of Ext2 with a journal.  This is the file system you want to use.  As for installing, when you get to the boot menu hit F6 and a line of text will appear at the bottom of the screen.  Delete the words "splash" and "silent".  This way as it boots it will tell you what is happening so we can determine what exactly is causing the issue.

---

### Post by Wizhk on 2007-03-11
Thx for the quick response. Ill have a go and see how it works out.

---

### Post by Wizhk on 2007-03-11
OK changed the drive over to Ext3

Ran the boot again with splash and silent removed. Here is where it seems to give up. 

<0> Kernel panic - not syncing: Fatal exception in interrupt

thanks

---

### Post by igknighted on 2007-03-11
Hmm, weird.  I think that refers to PCI devices.  What PCI devices do you have installed, maybe unplugging them during the install would help.  Also, run the disk check at the boot menu, mayb theres an error on the disc.

---

### Post by Wizhk on 2007-03-11
I will check the PCI devices. 

About the Disk Check.. I cant get passed monting the Root FOlder in the splash screen.

---

### Post by Wizhk on 2007-03-12
SO is there NO Ubuntu for me?

---

### Post by igknighted on 2007-03-12
Give v. 6.10 a try.  I had issues and 6.06 never installed right which 6.10 fixed, mayb it would solve your issues as well?  If nothing seems to work, give Opensuse or Mandriva a try.  The hardware detection on these versions of linux is different enough that you may not have any hardware issues at all.  The best advice I received when starting with linux was use the distro that supports your hardware best... it makes for the least trouble.  You might explore to find one that works better for you.

---

### Post by Wizhk on 2007-03-12
Alright.. Ill try 6.10 then the others.. thx.. ;)

---

### Post by igknighted on 2007-03-12
Look at this website: [www.distrowatch.com](www.distrowatch.com).  It is a great central resource for everything linux.  If you look on the right hand side at the "page htis rankings" it is a very crude approximation of the popularity of various distro's.  If you click the links on them you can get more info, links to their forums/websites and also reviews and screenshots.  You might find this useful if you are looking around.

---

### Post by Wizhk on 2007-03-12
Replaced my 12X CD Rom Drive with another faster drive and have now been able to boot all sorts of downloaded Distro's. 

Don't care for MEPI..

Ubuntu 6.10 boots, flashes some screwed up graphics then loads to a clean desktop then refreshes to load a log-in. then when I press enter to log in It tells me I already have an open panel and this happens over and over.

Ubuntu 6.06 I can operate fine at 640 X 480 resolution. My card is a VooDoo 3. I have read some things in the forums and think I can fix it but I am guessing that I have to do a full install to do so. I plan on doing a full install anyhow so this is not a problem. 

My question is is there an easy fix for 6.10's error or should I work on 6.06?

any tips on either solution please. :)

---

### Post by hyper_ch on 2007-03-12
For installing I rather recommend using the alternate install cd (and not the live-cd which you have now)...
[Exception to the rule above is if you want to test Feisty --> the alternate installer has still a bug with the partitioner...]

As for the partitions: Please delete that ext3 partition. During the install you will then be asked how you want to install it...

Either use largest free continouus space then ubuntu will use the diskspace that is not partitioned (see above regarding deletion of that ext3 partition) or use a manual setup with the following parameters:

- Swap Partition --> Make a partition about the double size of your ram and assign as filesystem type "swap"
- Root Partition --> Make a partition between 7-10GB in size, assign as filesystem "ext3" and select as mounting point "/"
- Home Partition --> Use the rest of the free space for the home partition. That's where your user settings will be stored (like your documents and configs and stuff...). Make it as filesystem also "ext3" and select "/home" as mounting point.

If you are unsure, select just, as pointed out above, "use largest continouus free space"...

---

### Post by Wizhk on 2007-03-12
Thanks for the Info. 

I am using Partition Magic to partition the whole drive. If I am to get rid of Ext3 I believe I have to make it something else then partition a portion upon install to ext3. Correct?

What should I change the main partition to if not ext3?

NTFS, FAT32??

This will be the only operation system on the computer.

Thanks again, and... 6.06 or 6.10 which, based on the errors listed will I have an easier time with?

:)

---

### Post by hyper_ch on 2007-03-12
You just delete the ext3 partition so that there is unpartitioned space :)

Alternatively you can make linux swap partition (2x size of your ram)
And 7-10GB "root" partition with "ext3"
And a "home" partition with "ext3"

If you make those partitions already then you will have to select the manually partition thing during the install... so that you just can assign them correctly.

---

### Post by Wizhk on 2007-03-12
OK.. thanks.

Now to DL the Alternative install iso..

I think I will stick with the 6.06 since I am fairly certain I can fix that problem.

---

