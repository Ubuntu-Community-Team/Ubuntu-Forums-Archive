---
title: "installing Adaptec SA1420 with one drive"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by gian on 2006-08-30
Hi,

I have an Adapted SA1420 controller, and one only SATA drive.

The drive is seen during BIOS scan, but Ubuntu does not show it.
I think there is a driver to be installed, or am I missing something ?

I cheched every repository and found nothing about SATA.

Adaptec site has drivers for SUSE or RedHat...

Anyone can help me ?

regards,
-GianLuca

---

### Post by John.Michael.Kane on 2006-08-30
gian have you tried entering the adaptec bios setup press [ctrl a] that should bring you the cards bios,and setup.

You should then be able the set the drive as you want.

Note: why are you trying to install one sata drive on a software raid card?

---

### Post by gian on 2006-08-30
..thanks for your kind reply!

the answer is a bit silly, but anyway...
I had these spares just sitting here in the office, and wanted to build a backup machine... so raid is not required.

I found this link on the Adaptec website:
[http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=AAR-1420SA&dn=Adaptec+Serial+ATA+II+RAID+1420SA](http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=AAR-1420SA&dn=Adaptec+Serial+ATA+II+RAID+1420SA)

The Rel Notes talk about cross-compiling for the kernel, and when I got through the doc I was shivering in fear... I don't know if I should try that... the repositories have spoiled me so much I started thinking it was almost like Windoze...

Also, what if Ubuntu auto-updates the kernel... I might not be able to access the drive anymore...

I tried a SATA card from Hamlet, but that one makes my Dell Poweredge sick and say "PCI BIOS failed".

Why is it so difficult to use a SATA drive with Ubuntu ?!
All new PC have SATA drives!

regards,
-Gian

---

### Post by gian on 2006-08-30
maybe I did not reply to your question...
Yes, I had tried ctrl-A, I can see the drive, I even formatted it.
During boot, the drive is listed as healthy.

---

### Post by pigor on 2006-08-30
You need to install the driver for the card to use it. I've been trying to do so but go to the part I can't figure out. I'm not even sure can it be recompiled for other distros other than SUSE or RH.
Would anyone more experience have a look? They are shipping the source code but also binary drivers, too. The script used for building the modules needs to know for binary drivers so I'm a bit confused now.

---

### Post by John.Michael.Kane on 2006-08-30
pigor all info leads to the fact that this card you both are having issues with is supported. you should be able to install the os,and format the drives.

you could using the [gparted-livecd]("http://gparted.sourceforge.net/livecd.php") use it to partition,and format the drive with the file system of your choice.


**Note:**are there any ide hard drives in these machines?
you may want to disconnect them,and try running the setup again.

---

### Post by pigor on 2006-08-30
It does seem that the card could work under Ubuntu. I want to use it to run 4 SATA hard disk in RAID10 configuration and didn't know that it's software RAID (Adaptec is very careful not to explain what HostRAID actually is although it's seems pretty clear now). Anyway, I got the latest driver source code which comes in packages in rpm package with very ugly written instructions and explanations. Now, it says to add the source code (including the binary drivers that come with it) to the kernel tree source and merge it with it using a build script. The only problem is that this script is written for RH or SUSE so I've been trying to figure out how to turn it to work with Ubuntu. I didn't have much time on my hands to play with and figure it out completely but I found that the script has some errors (as changed name convention in the directiories but not in the script itself). Currently I got to the part where it complains that it can not find the .config file (and it is not the one used for compiling the kernel as it know for that one). I'll try to fix it if possible.

---

### Post by John.Michael.Kane on 2006-08-30
pigor i found this i'm not sure this is source your using [**Linux Driver Source Code Downloads**]("http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=AAR-1420SA&dn=Adaptec+Serial+ATA+II+RAID+1420SA") though it might be. 

Also it does not seem this company has any plans to offer support for distro's other then what they have listed.

---

### Post by gian on 2006-08-30
SD,

thanks for your advice.

I am running GParted liveCD right now, and it's creating an ext3 file system on the 250GB drive.

I do not know if in the end of the process Ubuntu will mount the drive, but I cannot understand why, without any driver installed, GParted can see it and Ubuntu doesn't...

---

### Post by John.Michael.Kane on 2006-08-30
gian after gparted is done,and you try to install please post back the findings.

One other note I found a software raid howto. not sure if it would be of use.
[**Software-RAID-HOWTO**]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO-1.html")

---

### Post by gian on 2006-08-30
here I am.

Gparted ended the partitioning, and shows and ext3 250GB drive.

Ubuntu won't recognize it, though.
I mean that if I open System/Administration/disks I only see the scsi drive, and I'm back to square one...

<clueless>
-Gian

---

### Post by John.Michael.Kane on 2006-08-30
I'm not sure theres a way to get that card to work right now. short of trying fedora or suse.

---

