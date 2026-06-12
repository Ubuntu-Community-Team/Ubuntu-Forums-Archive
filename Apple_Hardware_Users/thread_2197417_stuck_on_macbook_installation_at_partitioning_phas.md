---
title: "stuck on macbook installation at partitioning phase"
date: 2014-01-03
forum: Apple Hardware Users
---

### Post by sharon2 on 2014-01-03
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]On my Snow Leopard Macbook, I want to have both systems - [/SIZE][/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]i.e.[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2] both ubuntu and my OS X .  My Macbook specs are: [/SIZE][/FONT][FONT=Georgia]OSX 10.5.8, 64 boot processor (2.2 Ghz Intel Core 2 Duo); 4GB memory (667 Mhz DDR2 SDRAM); HD capacity = 111.47 GB, Available = 51.04 GB.[/FONT]
[FONT=Verdana]I have successfully made a DVD (ubuntu-12-04.3-desktop-amd64.iso) and "tried" ubuntu 12.04 (love it!).  Now, I'm going for an "install" but I see I must first partition the hard drive.  I'm a newbie.  Questions: do I  "make a partition" with the native utility in my OS (i.e., with Applications/Utilities/Disk Utility.app)?  Do I have enough room for both systems?  _How big should I make the partitions? _  I've never made partitions before.  Thank you, Sharon2[/FONT]

So grateful for any help you can share.
Sharon

---

### Post by bapoumba on 2014-01-04
Thread moved to Apple Users.

---

### Post by varunendra on 2014-01-04
> **sharon2 said:**
> Questions: do I  "make a partition" with the native utility in my OS (i.e., with Applications/Utilities/Disk Utility.app)?
Even though GParted (available on the Live DVD) is quite good at partitioning, the above sounds a much better and safer option to me. I have no idea of dual booting with Macs, so am a bit mystified about the fact that the installer didn't offer to install Ubuntu "Alongside Mac" (maybe it is normal for macs, I don't know).

As the warning message in the screenshot shows, the previous partitions on the drive (and thus the mac installation on it) would be lost if you proceed with creating a fresh partition table on it. So to avoid such accidents, I'd also suggest to take a full disk image (using clonezilla or a native Mac application which can do that) on an external drive if you have one.

Although once the separate partition is safely created, you should get the option to install Ubuntu on it without affecting the existing Mac installation.

> Do I have enough room for both systems?  _How big should I make the partitions? _ 

The available space on the drive is more than plenty for Ubuntu, but obviously you'd want to keep some space for your Mac OS.

Default installation of Ubuntu takes less than 5 GB in total. But it is recommended to allocate it at least **10 GB** to allow enough room for future programs you may install + OS/data overhead while working.

For any serious usage, I'd recommend to allocate about 22-26 GB to Ubuntu + a separate 2 GB swap partition (or slightly larger than your RAM, i.e. 4 GB, if you wish to use "Hibernation" function on Ubuntu. Hibernation has been disabled by default since it often fails to work correctly and caused some driver issues, so can't say if it would work properly for you).

Lastly, as per your last screenshot, you were trying to install on '/dev/sda' which means the drive, not a partition on it. You need to create a partition and set it as the mount point for root (/) to be able to install Ubuntu on it. That would be represented as '/dev/sda1' (or some other number after "sda") where 1 means the first partition, 2-second... etc.

Oh, and like I said, I don't have much idea about drive/partition handling in macs, so I may be wrong, but as per the last screenshot (if you saved that change), the partition table on the drive was already overwritten and any existing partitions on it were lost. Hope you reverted/cancelled that scheme and saved your Mac OS.

For more help, I believe a screenshot of Gparted would be very nice.

---

### Post by sharon2 on 2014-01-05
Thank you, thank you Varun.  UBUNTU partition size is just what I needed to know.  And I so appreciated your additional remarks.  Fortunately, I did "CANCEL" before wiping myself out - so my OS X is still in tact.  I don't know what Gparted is ... else I would supply it.
Will try partitioning "native" (i.e. on my OS X) with your recommended generous size (26GB).  Is the extra swap partition (4GB)  useful for other things besides this unreliable hibernation that you mentioned?  Am wondering whether to do that too.  Anyway, fingers crossed - as I soldier on.    Sharon

---

### Post by varunendra on 2014-01-05
You're welcome! :)

Gparted is a disk partitioning program which is preinstalled on Ubuntu Live DVD. Assuming you are using default Ubuntu live DVD (not Xubuntu or Kubuntu etc.), you can open it by clicking on "Dash" button (the top button with Ubuntu logo on the left side panel) and type "gparted".

> Is the extra swap partition (4GB) useful for other things besides this unreliable hibernation that you mentioned? Am wondering whether to do that too.
Other than a place to save session information when hibernating, the swap space is just a 'Virtual RAM' on the disk. So with a 4 GB swap, the system would have 4GB (physical) + 4GB (swap) = 8 GB memory available.

Unless you are planning to run Virtual Machines, or are using heavy development programs, CAD designing, lots of heavy Video Rendering etc., you are probably never going to use even the whole 4 GBs of your RAM with the current version of Ubuntu. The OS + general use programs would be more than happy with the 4 GB RAM alone, so..... >

..the short answer - No. With 4 GB physical RAM, the additional 4 GB of swap space is not going to help anything other than hibernation.

Even 2 GB of swap would rarely be used (when you run long sessions, with probably 20-40 Firefox tabs open). Still it is recommended to **keep at least a 1 or 2 GB swap** ready just in case you need to run some heavy applications simultaneously, while there are tens of browser tabs are open.

---

### Post by sharon2 on 2014-01-05
Searching around, I just now came across this:  [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Detailed_How-To](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Detailed_How-To)
Looking at the section **Dual-Boot: Mac OSX and Ubuntu** seems to be exactly what I'm trying to do - but I'm scared - (am a newbie.) Will following this section preserve my OS X or will it partition my disk as if there was nothing on it and wipe out everything?  Sharon

---

### Post by varunendra on 2014-01-05
Nice explanation there, much better than someone like me could ever offer.

> Will following this section preserve my OS X or will it partition my disk as if there was nothing on it and wipe out everything?
Partition manipulation operations *(on 'Any' OS)* are always risky *(a slight mistake or accident can cause permanent data loss!)*. So a backup is always recommended before doing something like that, even if you are an expert on that *(experts do more accidents ;))*.

That being said, the process looks entirely safe to me. The OS X partition will always be there *(in step 3 of the "Quick Steps" part, it is the newly created partition that has to be deleted, so that you can create an EXT4 partition in its place)*, and once the additional partition for Ubuntu is created, the installation is quite straight forward.

You *may* (or may not) face a little difficulty in _booting Ubuntu the first time_ *(booting your Mac OS should still be no problem)*. If so, you may have to do some more reading on links given under "Fix the Partition Tables" section of the wiki page. I hope you won't need it though.

---

### Post by zircon_34 on 2014-01-10
How did the installation go with the help of your link you give in your post? Did you have any problems booting your system the first time after installation, did you use reEFit? I am also considering installing a dual boot on my mac but am little hesitant, as I don't want to make a mistake and get my system unusable. (also newbie here...)

---

### Post by sharon2 on 2014-01-10
To alexander.gysi - I haven't done it yet - (out of raw fear.)  But, I still intend to (using the link).  Will post my progress.  Sharon

---

### Post by zircon_34 on 2014-01-10
I tried this last year, installing was not so difficult, but when I booted the first time I could not start my system and of "fear" that my machine was finished, I reinstalled OSX and abandoned the project. 

What I learned. First of all, backup backup backup, time machine is easy. Having an install disc or live USB of OSX ready in case something goes wrong is handy and you can always boot you system, as it is installed on another partition, so it should still be there.

This weekend I might try the dual boot install again, I now know that before booting the first time into Ubuntu after install you may have to sync the partition tables in rEFIT, info that I did consider last year... Hopefully this time it will work. I was hoping someone had a positive experience with installing Ubuntu along OSX to give me confidence to try it.

---

### Post by sharon2 on 2014-01-11
Thanks for this Alexander.gysi.  I am eagerly hoping for your success and watching for your post. Please tell me what are the specs of your mac?  (Mine are: [COLOR=#000000][SIZE=2]Macbook 3,2; [/SIZE][/COLOR][COLOR=#000000][FONT=Georgia]OSX 10.5.8 (snow leopard), 64 boot processor (2.2 Ghz Intel Core 2 Duo); 4GB memory (667 Mhz DDR2 SDRAM); HD capacity = 111.47 GB, Available = 51.04 GB.)     Sharon[/FONT][/COLOR]

---

### Post by zircon_34 on 2014-01-11
I have a basic Macbook air 5,1 (11inch mid 2012), intel core i5 1.7Ghz dual core, 4Gb Ram, 128 SSD. OSX 10.9.1 (Mavericks), trying to dual boot with Ubuntu 10.3.

---

### Post by zircon_34 on 2014-01-12
Ok did it! It works fine, wireless, keyboard, trackpad, sound, even the dim buttons for the lights on the keyboard work! But there were little tricks to consider, so I had problems for the partitioning and with the boot loader. I had to install it twice because the first time I could not boot into Ubuntu. Anyways, you still can boot into MacOS so there was no problem for trying again. The only thing was that I had to deactivate file vault, else the install would have been more complicated... 

you may check my [thread]("http://ubuntuforums.org/showthread.php?t=2199210").

---

