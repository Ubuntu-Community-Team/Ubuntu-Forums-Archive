---
title: "Is my ubuntu unstable?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-07
After finaly getting ubuntu to load up on my computer I have had the following issues:

Installing ubuntu changed my slave drive and took about 40gb without me understanding why or how this happened

Sometimes it will not load and I have to switch off and try again.

When looking as screen savers the screen would go blank and then ask me for name and password before returning to the desktop.

When I went into a folder to look around (XP folder) the entire operating system froze.  I took the dog for a walk for well over an hour and returned to a frozen screen.

I then tried to boot into XP and nothing happened.

I then tried to boot XP in safe mode and nothing happened.

I then tried to boot into XP, got the welcome screen which then changed to the ubuntu screen which loaded ubuntu instead

I then finally got into XP but some how my network card was affected and I had to tinker around to get back onto the internet.

Being new to Linux style operating systems, is this a normal introduction or have I been very unlucky?

Would I get better results if I used an earlier version than 7.04?

I really would appreciate any advice as to why all this may be happening.

Cheers

---

### Post by vanadium on 2007-05-07
It is not a normal experience. I installed Ubuntu Edgy and it installed and ran without a glitch.

The "blank screen + password" is the default behaviour of the screensaver. In System - Preferences -Screensaver, you can disable the "locking" or even inactivate the screensaver.

If it took 40 Gb "without your understanding" then you must ask yourself whether you did not overwrite the XP partition? For the rest, it sounds to me as if there is a problem with your hardware. It could be defective, or it could hardly meet minimal requirements. When posting such issues, it is wise to provide some info on your system.

---

### Post by mikewhatever on 2007-05-07
How did you do the partitions set up during the installation? Is Windows on your primary drive and Ubuntu on slave?

---

### Post by the lemming on 2007-05-07
> **vanadium said:**
>  When posting such issues, it is wise to provide some info on your system.


Hope this helps

AMD 64 3400+ processor 2205MHz
2gb RAM
Nvidia GeForce FX 5700 Graphics card
1 DVD Re-write drive
1 DVD Read only drive
2 Hard Drives 112GB with several partitions all of which are NTFS
2 External Hard Drives with several partitions and all of which are NTFS
Belkin 802.11g wireless card model F5D 7000uk
Medion TV-Tuner 7134 MK 2/3


Cheers

---

### Post by mikewhatever on 2007-05-07
In Ubuntu, can you go to Application>Accessories>Terminal and post the output of the following command > sudo fdisk -l

---

### Post by vanadium on 2007-05-07
That looks like a more-than-up to date system with plenty of RAM and a 64 bit processor. Did you install the 64 bit version of Ubuntu?= ("64bit AMD and Intel computers", see [http://www.ubuntu.com/getubuntu/download)](http://www.ubuntu.com/getubuntu/download)). If not, then I am not sure to what extent a standard 32 bit version (Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)) can run reliably on 64 bit processors (I expect it would, but then I do not really know).

---

### Post by Sef on 2007-05-07
> 2 Hard Drives 112GB with several partitions all of which are NTFS
2 External Hard Drives with several partitions and all of which are NTFS

What file system did you save your Ubuntu on (ext3, reseifers, or other)?

---

### Post by dptxp on 2007-05-07
7.04 is fine, very fine with your hardware. You can use 64 bit, 32 bit sometimes can give some problems.

You most probably made mistake at time of partitioning.

Go for manual partitioning. Resize, format / as ext3 (4 to 8 GB), 2 GB for swap, and you need FAT32 or EXT3 format for data. Make sure you check the partitions to be formatted and not format others.

REINSTALL.

---

### Post by the lemming on 2007-05-07
> **Sef said:**
> What file system did you save your Ubuntu on (ext3, reseifers, or other)?


In the end I put my master drive back to one great big partition, which was defraged (in XP).  I then installed ubuntu and let it choose the most appropriate filing structure.  That worked.

As for my OP I installed the 32 bit version.  However I am more than willing to install the 64 bit version if people think that this will solve any problems.

At the moment I am in XP, so that I can access the internet, and the Disk Manager gives the following info
 Primary disk

C: named XP  61.37gb NTFS (primary)
Unknown partition 48.31 gb   (primary)
Unknown partition 2.11gb      (logical drive)

Slave disk
D: named Ghost backup 30gb NTFS (primary drive)
H: named disc two 41.39gb NTFS (primary drive)
Unallocated 40.40gb (this happened during a failed attempt to install ubuntu yesterday)

A little later I will try the Terminal and type in sudo fdisk -l
I have never done this before so wish me luck.

Must go now because the other half thinks I'm ignoring here too much now.

Cheers

---

### Post by antoz on 2007-05-07
you seem to have had a lot of problems, what I can't understand is that you say you have Ubuntu installed but all your partitions are ntfs? there has to be at least one ext 3 and a swap.
Why don't you post a screen shot of your partition table using the Gnome partitioner, to get your picture ->applications->accessories->take screenshot and post it here so someone can have a proper look. I you can't access the net in Ubuntu save the picture to a usb flash drive, if you can't boot Ubuntu boot with the live CD.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/) tutorial for dual boot including vista

Some good links

---

### Post by antoz on 2007-05-07
[QUOTE=

At the moment I am in XP, so that I can access the internet, and the Disk Manager gives the following info
 Primary disk

C: named XP  61.37gb NTFS (primary)
Unknown partition 48.31 gb   (primary)
Unknown partition 2.11gb      (logical drive)

Slave disk
D: named Ghost backup 30gb NTFS (primary drive)
H: named disc two 41.39gb NTFS (primary drive)
Unallocated 40.40gb (this happened during a failed attempt to install ubuntu yesterday)
[/QUOTE]

[B]Unknown partition 48.1 gb is most likely your Ubunti install
Unknown partition 2.11 is most likely your swap[/B]

That unalocated space on your slave drive you can reclaim with the partition editor on the live CD or you could create a Fat 32 partition there to share between Windows and Ubuntu

---

### Post by the lemming on 2007-05-07
> **mikewhatever said:**
> In Ubuntu, can you go to Application>Accessories>Terminal and post the output of the following command

I am typing this from my laptop.

I put the command you asked and fot the following

unable to open -
frank@frank-desktop:~$



is that good or bad?

---

### Post by the lemming on 2007-05-07
> **the lemming said:**
> I am typing this from my laptop.

I put the command you asked and fot the following

unable to open -
frank@frank-desktop:~$



is that good or bad?


The entire system is frozen now.  How do I get out of the Terminal?

Nothing at all works, mouse or keystrokes

---

### Post by antoz on 2007-05-07
you could try Alt F4

---

### Post by mikewhatever on 2007-05-08
That command (sudo fdisk -l) does nothing but prints out the partitions set up. I guess the fact that it failed is not a good sing, but not quite sure why it did.

---

