---
title: "Ubuntu 7.10 (Gutsy Gibbon) Tribe 4 First time"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by rubab on 2007-08-10
I am a total newbie in the Ubuntu world. I have been thinking of using Ubuntu for a very long time and i believe now is the time. Recently Windows XP gave me shock when i selected just one partion(J Drive) and selected Delete and Stupidsoft XP deleted my other two partitions in which i had all the files,programs i have been downloading for the last two years. When i recovered the partitions all the file was corrupted in other word totally destroyed.
 I hope i am giving you enough info so that you can help me.

This is my PCs Congfiguration:
User: Administrator
Operating System: Microsoft Windows XP Professional 5.01.2600 Service Pack 2
Report Date: Friday 10 August 2007 at 13:54
System Summary	 
Mainboard 	Intel D915GAV
Chipset 	Intel i915G
Processor 	Intel Pentium 4 530J @ 3000 MHz
Physical Memory 	1024 MB (2 x 512 DDR-SDRAM )
Video Card 	ATI Technologies Inc Radeon X1650 Series
TV Tuner 	AVerTV GO 007 FM Plus
Hard Disk 	HDS728080PLA380 (82 GB)
DVD-Rom Drive 	SONY CD-RW CRX300E
DVD-Rom Drive 	ASUS DVD-E616A3
Monitor Type 	LG Electronics E700SH - 17 inches
Network Card 	Realtek Semiconductor RT8139 (A/B/C/810x/813x/C+) Fast Ethernet Adapter
Operating System 	Microsoft Windows XP Professional 5.01.2600 Service Pack 2
DirectX 	Version 9.0c (July 2007)

From which site will i find the Drivers for all my hardware. I search for the driver for ATI Technologies Inc Radeon X1650 Series on ATI Homepage but the Linux version of the driver for my Video card was not there. I am not sure is there a driver for my TV Tuner i  mean Linux version.

At the moment i am downloading Ubuntu 7.10 (Gutsy Gibbon) Tribe-4.
As I am a total newbie i want to know that is it possible to download the softwares separately with the necessary libraries. Because i use a broadband connection for a few months in a year & after every time when i disconnect my broadband for a few month i format my C drive(I have 5 drives D:Games,E:Soft...) and install a fresh copy of windows and then other softwares.

I want to know that if i format  only my C drive will the older version of ubuntu be erased?
Is there a way i can download all the drivers and softwares separately so that after the installion(Without internet) of ubuntu i can install the drivers and software which i backed up earlier on D drive.

I am waiting for your replies.
Thanks in advance.

---

### Post by misfitpierce on 2007-08-10
Firstly seeing as how you are new to the Ubuntu world I would highly not recommend installing Gutsy Gibbon at this time. 

 Use 7.04 Feisty as it is more stable and not still in alpha/beta stage. Gutsy is being tested and you are more than likely to hit quite some issues.

---

### Post by BaffledMollusc on 2007-08-10
> **rubab said:**
> From which site will i find the Drivers for all my hardware. I search for the driver for ATI Technologies Inc Radeon X1650 Series on ATI Homepage but the Linux version of the driver for my Video card was not there. I am not sure is there a driver for my TV Tuner i  mean Linux version.

Linux is a bit different from Windows when it comes to drivers. Usually all the drivers are already built into linux, so you won't have to install them. The two exceptions may be the video card and the TV card.

You will probably need ATI's proprietary driver for the video card, since I'm not sure if an open source driver exists. This ATI driver can easily be installed from Synaptic (an Ubuntu application you use to find/install software). I'm not sure about the TV card, though.
> 
At the moment i am downloading Ubuntu 7.10 (Gutsy Gibbon) Tribe-4.

That's probably not a good idea. 7.10 has not even reached beta yet, and is still a test version. The final version is due in October. Until then, the current version of Ubuntu, 7.04, would be a much better idea. 
> 
As I am a total newbie i want to know that is it possible to download the softwares separately with the necessary libraries. Because i use a broadband connection for a few months in a year & after every time when i disconnect my broadband for a few month i format my C drive(I have 5 drives D:Games,E:Soft...) and install a fresh copy of windows and then other softwares.

I want to know that if i format  only my C drive will the older version of ubuntu be erased?

I'm not sure what you mean. Linux uses partitions, not drive letters (C, D etc like Windows). What you can do is put all your personal files (i.e. your home directory) on one partition, and install Ubuntu on another. That way you can install a new version of Ubuntu over the old one without destroying all your user files.
> 
Is there a way i can download all the drivers and softwares separately so that after the installion(Without internet) of ubuntu i can install the drivers and software which i backed up earlier on D drive.

Yes. Any packaged software you download and install is cached in some directory (/var/apt/cache, maybe? I'm not sure). If you copy this directory before deleting it, you should be able to keep any software you've installed.

---

### Post by rubab on 2007-08-10
Thanks misfitpierce & BaffledMollusc for your replies.

---

