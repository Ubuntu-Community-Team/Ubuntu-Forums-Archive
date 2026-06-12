---
title: "Unable to install Linux (Not just Ubuntu)"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Vitz on 2007-10-25
Well, today I received my laptop. First thing I did was getting rid of Vista of course (full NTFS 4096 reformat), and pop in the new 7.10 release of Ubuntu.

Much to my displeasure, the install disk wouldn't work. It would go into the boot menu, where I could select what I wanted to do and stuff. A normal installation was what I tried first, which resulted in the by now well-known bug where you simply get a black screen and the computer does nothing anymore. I've been reading through the rather massive thread about this, and though I tried pretty much every solution there (well, the ones I could understand, I'm very new to Linux), but to no avail. Understanding that this was supposed to be a 7.10 bug only, I began downloading Feisty (7.04). In the meanwhile, I tried installing Fedora Core 6 ''Zod'' to see if that would have any success. However, this installation also came to a halt at one point, which I couldn't explain and decided that the disc was just crappy.

And so here I am. I just burned Feisty, and for some reason it's giving me the exact same errors as 7.10 did. I'm pretty baffled and have thus far tried everything I can think of.

Using the ''nosplash'' command I was able to see what the problem was, but being new to this, it's like Chinese to me.

This is what I get:


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) **[     60.429378] hda: drive not ready for command**

The line I made bold appears another 9 times after that, each time with a different number in front of it.


Anyway, ''drive not ready for command''. What does this mean, and is this the problem? And if so, is there a way I can fix this?

Thanks in advance for any replies.

---

### Post by dptxp on 2007-10-25
Laptop model, hardware details please.

---

### Post by Vitz on 2007-10-25
Ah yes, of course. Sorry about that.

Fujitsu Siemens Amilo Xa-2528
AMD Turion TL-56 @ 1800MHz (Dual core)
2GB DDR2-667 15-5-5-5 RAM
nVidia GeForce Go 8600 256 MB DDR2 up to 767MB TurboCache
160 GB SATA 5400 rpm


And another thing I think is worth mentioning, above the errors I get, it first tells me ''PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0''.

---

### Post by ItsMitsHere on 2007-10-25
can u run live cd perfectly?

---

### Post by taurus on 2007-10-25
Did you burn the CD yourself?  Did you remember to run a checksum before you burnt it and how fast did you burn it?

---

### Post by Vitz on 2007-10-25
The Live CD runs like it should. It simply stops after I want to install.

I did burn the CD myself, at 4x. As recommended. I doubt this is the problem, seeing as I've burned 7.10, 7.10 Alternative and 7.04 now.

However, 7.10 Alternative did show signs of life. I chose for the text-based installation, and it allowed me to choose my language and country, as well configure my keyboard. After that, it would look for drivers and such for the CD drive etc. The necessary stuff for the installation I guess. But when that's done, the whole thing freezes up again. The next step of the installation simply never appears.

---

### Post by ItsMitsHere on 2007-10-25
if live cd works perfectly, there might not be any problem with the hardware except the harddisk. try DSL (Damn Small Linux). If it can be installed on the hard disk then try ubuntu. if even DSL can't do the magic then try to install any windows and then try installing ubuntu over windows with live cd.

---

### Post by Vitz on 2007-10-25
Well I went ahead and installed Windows XP, which went just fine. Then I ran the Ubuntu setup. It said I had to reboot, so I did. Then the whole problem started right over again.

Doesn't Ubuntu like NTFS drives or something? Should I try FAT32?

---

### Post by LaRoza on 2007-10-25
I used a text based installer when my laptop did the same thing. It worked perfectly once installed (well, sort of, but the problems were easily fixed)

---

### Post by mivo on 2007-10-25
Ditto. The Alternate CD worked when the Live CD's installation failed (on one machine).

---

### Post by xaco1234 on 2007-10-25
you installed it on a ntfs partiption`?

---

### Post by Vitz on 2007-10-25
Yes, I did. Judging by the way you said that, I think I was very stupid when doing that :P
About the Alternative disc, I described how that ends up a few posts back. It doesn't take me much further than the LiveCD does.

---

### Post by xaco1234 on 2007-10-25
use the ext3 file format and it shoud work, don't think installing a linux distro on an ntfs partition will work

---

### Post by Vitz on 2007-10-25
God I feel like a tard.

Just made a new partition in Ext3. Let's see how this goes.

Thanks for the help :)

---

### Post by mivo on 2007-10-25
Yes, the root partition of Linux cannot be formatted in NTFS. ext3 is not the only choice, but probably the "best" for most users.

---

### Post by halitech on 2007-10-25
If Ubuntu (or any version of linux) is going to be the only OS on the machine, it should at least allow you to get to the partitioning stage, just tell it to use the entire disk and it should format and partition the entire drive. If not, get the gparted cd and use it to format in etx3 (as suggested above) and then it should install properly.

---

### Post by Vitz on 2007-10-25
> **halitech said:**
> If Ubuntu (or any version of linux) is going to be the only OS on the machine, it should at least allow you to get to the partitioning stage

Sadly, it doesn't...The text-based installation (the only that works) doesn't go further than detecting drives. It does this, and then simply hangs at the blue background of the installer.

I'm burning the install disc with my other burner and a different burning program. I guess it's a last resort. If this doesn't work, I'd probably have to get technical. I'm experienced in Windows and stuff, but I don't know anything about Linux just yet so getting technical with it will probably end up in frustration.


Edit: Well, the first disc turned out to be fine. The new one doesn't help me either, so I'm officially stuck.

---

### Post by xaco1234 on 2007-10-25
you tried installing it on an ext3 partition?

---

### Post by ItsMitsHere on 2007-10-25
> **Vitz said:**
> Well I went ahead and installed Windows XP, which went just fine. Then I ran the Ubuntu setup. It said I had to reboot, so I did. Then the whole problem started right over again.

Doesn't Ubuntu like NTFS drives or something? Should I try FAT32?

i think ubuntu should be installed on an ext3 partition. during the installation process (which starts when you double click the install icon on the desktop while running the live cd) the gnome partitioning tool asks about where u wish to install ubuntu, if you choose manual and then u can format the partition of your choice to ext3 by selecting the partition and clicking the edit partition button below, and the partition should be mounted at / from the dropdown menu. you will also need a swap partition of around 1 gig. please give full details of how u go about the installation process and at which point it hangs...

---

### Post by tweistein on 2007-10-25
hello - vits.. You sholud definiteley use fat32...:-)

---

### Post by Vitz on 2007-10-25
I tried installing with an ext3 partition present. This didn't work, however.

To make it clear: I can only get into the installation using the Alternative version of 7.10. However, I don't get far, seeing as I'm only able to select where I live, what keyboard I have, and then it starts detecting drives. It gets to 100% detection of drives, after which it simply hangs and only shows the blue background of the installer. I can't get past this. I can't even reach the actual installation this way because it stops before I can even select a partition to install it on.

---

### Post by jbonll05 on 2007-10-25
In August I bought a Seagate 250g usb harddrive. It did not work with 7.04 or 6.06LTS. I checked the drive and a message said it was a "NTFS drive". AS a guess I reformatted it to Fat32 and it runs with my 3 Ubuntu machines as well as an HP laptop with XP or Ubuntu Gutsy on a switched hard drive. The Seagate is a mass storage device, not specifically a hard drive; however it might work the same way. The install maybe compatible with fat32. 
JB

---

### Post by Vitz on 2007-10-25
But still, shouldn't it at least take me to the screen to select the partition?

---

### Post by xaco1234 on 2007-10-26
you can't get to wich partition you want to have it installed on, on any linux live cd/install cd?

---

### Post by Threbus5 on 2007-10-26
Hmmm.

Have you tried 
1. Make a reliable backup of your Windows OS. One that will boot from CD/DVD. If the entire computer goes "South for the Winter" at least you can restore an operating condition. (Remember though, if you format to an ext2 or ext3 it will be necessary to use fdisk etc to restore an NTFS format for a Windows restore.)

2. start and run from the Live CD

3. Will the Live CD will allow you to format the hard drive from the disk manager? If it will not, then proceed to #4. 

4. Open a terminal window and  format the hard drive to a Linux friendly format (Fat32  or one of the extensibles). Although the install CD should present the option to format the drive, you appear restricted from that.

See this resource for a terminal window Linux HD formatting process: [http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html)

5. After the hard drive formats, install Ubuntu from the Live CD.

Take care

---

### Post by Vitz on 2007-10-26
Well, I reformatted a partition into FAT32 (Two, actually), but this sadly didn't make a difference.

However, I think I might have found the problem. My DVD drive. I tried installing Fedora Core 7 yesterday, and it said it couldn't install because it didn't have the drivers from my DVD drive. Seeing as the text-based installer of Ubuntu stops right after detecting the drives in the system, I'll assume it's also not recognizing my drive. It just doesn't bother to tell me and freezes up instead.

So yeah...I have no idea what drivers I need for my drive, nor do I have an external CD/DVD drive I could use. The only flash memory stick I have can only carry 512MB, which isn't sufficient either. So...am I screwed here until I manage to buy either an external drive or a larger memory stick?

This would also explain why 7.04 is giving me the same errors.

---

### Post by bsh on 2007-10-26
i doubt it's your dvd drive. if the lappy runs fine from the live cd, then your drive works.
wrongly connected ide devices (ie. hard disk and dvd on the same cable, jumpered badly) can cause problems indeed - but since it's a lappy this may not be a problem.
dvd drives use a generic driver, every single piece of them i have had, worked with generic drivers.
i think the problem might be your hard drive not beeing detected properly. maybe the lappy's chipset isn't supported by ubuntu yet or something.
the easiest way to find this out and to make proper partitions, is: boot up with the live cd. when you get to the desktop, find "gparted" in the start menu and run it. it's the partitioning tool with the graphical user interface. if you don't see your drive listed in it - then this is the problem.
if it recognizes it, however, and if you are already there, you could remove everything from the drive (every partitions, except if you have a service partition which is usually a very small hidden partition). create new partitions: at least one partition for /, should be at least 2gb but i use 5gb. use ext3 as the filesystem on this. and one swap partition too, should be  roughly the amount of your physical ram (2gb?), but if it's bigger it's no problem. and i suggest you to make a separate partition for your /home.
if you are succesful and all partitions are done, try to install on them.

---

### Post by Vitz on 2007-10-26
> **bsh said:**
> i doubt it's your dvd drive. if the lappy runs fine from the live cd, then your drive works.
wrongly connected ide devices (ie. hard disk and dvd on the same cable, jumpered badly) can cause problems indeed - but since it's a lappy this may not be a problem.
dvd drives use a generic driver, every single piece of them i have had, worked with generic drivers.
i think the problem might be your hard drive not beeing detected properly. maybe the lappy's chipset isn't supported by ubuntu yet or something.
the easiest way to find this out and to make proper partitions, is: boot up with the live cd. when you get to the desktop, find "gparted" in the start menu and run it. it's the partitioning tool with the graphical user interface. if you don't see your drive listed in it - then this is the problem.
if it recognizes it, however, and if you are already there, you could remove everything from the drive (every partitions, except if you have a service partition which is usually a very small hidden partition). create new partitions: at least one partition for /, should be at least 2gb but i use 5gb. use ext3 as the filesystem on this. and one swap partition too, should be  roughly the amount of your physical ram (2gb?), but if it's bigger it's no problem. and i suggest you to make a separate partition for your /home.
if you are succesful and all partitions are done, try to install on them.

The Fedora installation however, does recognize the hard drive (it tells me to select a partition which carries the Fedora images because it can't get them off the DVD, apparently, which is what I'll try next). But not the DVD drive, it seems. That's what troubles me.

About the Live CD, I have probably been unclear about that. When I said it worked perfectly, I meant it works perfectly up until trying to boot/install Ubuntu. I can't actually get into Ubuntu/Linux.


On a sidenote, many thanks to everyone who has replied thus far. I really appreciate the help.

---

### Post by mivo on 2007-10-26
Just to clarify this: The root partition also cannot be installed in a FAT32 file system. I don't have the documentation handy, but the root partition may only be formatted in a limited number of Linux-specific file systems, i.e. ext2, ext3, ReiserFS and some others (but not FAT32, NTFS, etc.). This only applies to the root partition. (However, this doesn't seem related to the trouble you experience.)

---

### Post by Vitz on 2007-10-26
Yeah, I tried using ext3, but no luck.

---

### Post by Calash on 2007-10-26
I am assuming this is a brand new vista compatible laptop?

Very odd, the busybox error is the same as we see on the older PowerPC based systems.  I am beginning to wonder if there may be a BIOS issue with that model.  It may be worth the time to see if there is a BIOS update and apply it to see if it helps at all.

---

### Post by Vitz on 2007-10-26
> **Calash said:**
> I am assuming this is a brand new vista compatible laptop?

Very odd, the busybox error is the same as we see on the older PowerPC based systems.  I am beginning to wonder if there may be a BIOS issue with that model.  It may be worth the time to see if there is a BIOS update and apply it to see if it helps at all.

Yep. Brand new Vista.

I'll see if there's a new BIOS out. And pray it works.

---

### Post by Calash on 2007-10-26
Having a random thought here....

In your BIOS, under the hard drive settings, can you set something called "Compatibility Mode", or something with a similar name?  On our new Dell systems at work we had to adjust the SATA drives from Normal to "Combination" to get our image process to work.  This has since been fixed, but the error does sound similar.

---

### Post by khurrum1990 on 2007-10-26
Hi, I would suggest that u give OpenSuse 10.3 and Mandriva Linux a try. If neither of them works which I highly doubt then just use Windows. Download OpenSuse 10.3 from [http://en.opensuse.org](http://en.opensuse.org)
Use bit torrent to download to ensure u get an uncorrupted download. Then what u have to do is burn it onto a cd and verify the files after burning. This is the best way. Linux should work this time.
Good Luck and take care!

---

### Post by Vitz on 2007-10-26
No BIOS updates available :/

I'm trying OpenSUSE as we speak, and it's having the same problem as all the others. It can't recognize the DVD drive apparently because it fails to read the files off of it.

Edit: I noticed OpenSUSE offers a deliverance of the files through FTP and HTTP, so I'm currently installing it using FTP. Does Ubuntu have something like this as well (once again, I'm new to this)?

---

### Post by jryprt on 2007-10-26
Here is something to try . Install XP again & try the Wubi installer for ubuntu 7.04  [http://wubi-installer.org/](http://wubi-installer.org/) 
It runs on the ntfs partition if it works you can put it on its own  partition with LVPM: Upgrades Wubi installs to real Ubuntu installs with dedicated partitions [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by Vitz on 2007-10-26
> **jryprt said:**
> Here is something to try . Install XP again & try the Wubi installer for ubuntu 7.04  [http://wubi-installer.org/](http://wubi-installer.org/) 
It runs on the ntfs partition if it works you can put it on its own  partition with LVPM: Upgrades Wubi installs to real Ubuntu installs with dedicated partitions [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Just wiped the entire HD again before installing openSUSE :P

However, I will be using this on my desktop PC. Thanks.

---

