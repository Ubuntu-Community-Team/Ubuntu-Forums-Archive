---
title: "problems setting up dual boot with xp/ubuntu 7.04"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by legoman666 on 2007-08-19
First off, I am a complete n00b to linux. I just booted into it for the first time like 2 hours ago.

My windows xp x64 installation is on a raid 0 array of 2 sata drives. I booted the ubuntu live CD, messed around for a bit, decided that I'd install. So I click install and continue through the set up and get to the part where you tell it where to install to. Now, I have 8 physical hard drives in this computer, but there are 2 raid 0 arrays, each with 2 drives. so thats 6 logical drives. There are 2 sata WD 36gb raptors (in raid0), 3 sata 250gb (2 in raid0, 1 single. the single 250 is where i want to install to), 2 ide 80gb, and 1 160gb ide drive.

the problem is, the partition set up manager thing detects physical drives, not logical. So I spend like 20 minutes trying to decide which of the listed 250gb drives is the single one. I finally decide that its the last one in the list, and install ubuntu onto that. 

Installation is painless and completes quickly. Tells me to reboot and take the cd out of the drive. I do just that. And of course, when the computer reboots, it boots into win xp. I went to the boot.ini file in xp and there was nothing else there (of course). So, I rebooted again and changed my default hard drive to the one I installed ubuntu on. When it tries to boot from that drive, I get an error like "error loading operating system" or something similar.

So i put the install CD back into the drive and boot back into the Live version. I click install and get to the partition setup again. Now the partition setup detects the previous install of Ubuntu, but i am unable to boot into it. And this is where I am now, sitting in the live version, trying to figure out what the hell to do :D

any ideas? There are probably a million other posts like this, but none of them seemed to apply to me when I searched.

---

### Post by kidcharles on 2007-08-19
Do you think you have enough drivespace? :P

I think the problem might be that the grub bootloader was installed on one of your many drives, but is in a place that is not being found based on your motherboard's boot settings.

> 
So, I rebooted again and changed my default hard drive to the one I installed ubuntu on.


I assume you mean you changed the drive to boot from on the BIOS of your motherboard?

I think you definitely installed Ubuntu fine since the LiveCD is detecting it. You might want to try installing again and paying close attention to where the grub boot loader is installed.

---

### Post by legoman666 on 2007-08-19
heh I have much more drive space than that. My other computer has 3x120gb and the htpc has 1x120 and 1x320. :D Can't have too much space.

Anyway, I don't recall anything during the isntall about grub. And I just checked the root of all of my drives and I don't see grub anywhere.

And yes, I mean I changed which drive the mobo boots from.

---

### Post by BoneKracker on 2007-08-19
The bottom line is that you need to designate the device onto which you installed Linux as the boot disk in your PC's BIOS.  Then make an entry in the Linux bootloader's configuration file allowing you to choose between the two operating systems.  The booloader used by Ubuntu is called GRUB.  The file is /boot/grub/menu.lst and contains an example (look for the word "chainload"; uncomment and modify that entry to create a menu option allowing you to choose to boot XP).

Alternatively, you could use the Windows bootloader, but it lacks just about all muti-boot functionality.

You can choose to install the Linux bootloader onto the disk that is currently your boot disk (in which case it will over-write the master boot record placed there by Windows), but it is not installed there by default by the Ubuntu installer.

It is probably best to initially just switch your boot disk in the BIOS, leaving the Windows bootloader's crap alone in the other MBR so you can use it to boot if you screw up Ubuntu.  Once you have decided your Ubuntu is set up the way you want it, where you want it, and that you want to keep it, you can learn how to put the bootloader where you want.

A couple of notes regarding RAID.  Linux does recognize RAID devices, but only real ones.  If you have a "fakeRAID" device (i.e. one of the inexpensive SATA controllers found on a lot of motherboards produced in the last couple of years), then Linux will only "see" the physical disks.  "FakeRAID" relies upon the CPU for its processing, so it is essentially redundant with the RAID functionality already built into Linux.  If you do want to access a "fakeRAID" array, you can do so by installing the software for it (which is available in the Ubuntu repository).  I think the package is called dmraid.  This provides a "device mapper", which basically creates a logical device "md-something" that actually corresponds to the vendor-specific controller's concept of the multi-physical-device array.  Don't be intimidated, there is lots of information available in these forums and in the Ubuntu wiki about how to set it up.  Basically, here is what you should know at this point: if you want to dedicate an entire to array to Linux, it's probably best to use the Linux RAID functionality -- setting this up can be easily done at install time.  If you want to use an existing SATA RAID (i.e. "fakeRAID") array from within Linux, you need the driver mentioned above for Linux to recognize it.  If you want to actually boot from such an array, it's kind of a pain in the *** to set up, but there is a howto in the wiki.  A haven't read anything anywhere that says fakeRAID is faster than Linux RAID (and I've seen some unscientific commentary, which I ignore,  that it's slower).

---

### Post by legoman666 on 2007-08-19
I am at the point in the installation where you choose the device for boot loader installation. The default is "hd0" Since I have 8 drives, I have no idea which one that is. If I have to venture a guess, I'd say it was the raid 0 array that win xp is installed onto. But I'm not really sure.

---

### Post by BoneKracker on 2007-08-19
GRUB has become something of a rite of passage for new Linux users (because they often are dual-booting when they first try Linux).  GRUB is not well-documented and is confusing because it uses notation that is unfamiliar to Windows and UNIX users alike.

I strongly recommend you take a time out to read just a bit of documentation on GRUB.  I've summarized a couple of key points below, and placed a link to one relatively-friendly piece of documentation at the bottom.  I believe there is also some in the Ubuntu wiki.  Be patient, this is something everybody has to suffer through.  You do learn some very reusable things in the process, though.

In Linux, drives are referred to like this:

hda = ide controller 1, disk 1
hdb = ide controller 1, disk 2
hdc = ide controller 2, disk 1
hdd = ide controller 2, disk 2

sda = scsi (or sata) disk 1
sdb = scsi (or sata) disk 2
etc.

There are others but you get the idea.

Now, "devices" may be entire drives, but we generally mean "partition" when we say "device" in the context of storage.  So "devices" go like this:
hda1 = ide controller 1, disk 1, partition 1
sdb3 = sata disk 2, partition 3
etc.

The above, again, is the notation used throughout Linux.  GRUB, however, uses a different notation.  This is because GRUB (being the "Grand Unified Boot Loader") is intended to be portable across a large number of platforms, which use many different notations to designate devices.  So, GRUB uses it's own notation for GRUB commands and the parts of the GRUB configuration file that are used to construct GRUB commands.  

The confusion is exacerbated by the fact that GRUB uses the platform's native notation (in our case, Linux notation) in the parts of the GRUB configuration file that are used to construct Linux commands.

In GRUB's notation, counting starts from zero, and all drives are "hd".
hd0
hd1

Here is a link to some documentation.  You can google for more 'grub documentation' and search the Wiki.
[http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html)

If you really want to become intimate with GRUB, you can later set up your system to actually boot from one of your sata raid arrays (in which case you have devices that look like "/dev/mapper/nvq0e98trq0ew"  :)

---

### Post by legoman666 on 2007-08-19
Hm, I got it working but by more or less bypassing grub. I just change the boot drive in the bios when I want to switch from xp to ubuntu.

---

### Post by BoneKracker on 2007-08-19
Yes, that works too, if you don't mind booting up twice every time.  :)

And that confirms that you did put the GRUB stage 1 onto a different MBR than the Windows device.

It's really simple, though, to add the little chainloader entry to menu.lst.  All it does is call ("chain-load") ntldr, you're just bypassing the stage 1 part that's in the MBR written to by Windows.  Just a matter of convenience.

---

### Post by BoneKracker on 2007-08-21
You might also want to read this.  According to this (not sure how factual this is) some people have reported difficulties with GRUB when using both PATA and SATA drives, and this suggests some work-arounds.

[http://linuxgazette.net/141/anonymous.html](http://linuxgazette.net/141/anonymous.html)

---

