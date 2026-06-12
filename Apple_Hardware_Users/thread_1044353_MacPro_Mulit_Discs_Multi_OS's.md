---
title: "MacPro Mulit Discs Multi OS's"
date: 2009-01-19
forum: Apple Hardware Users
---

### Post by jltnol on 2009-01-19
So I have a MacPro and have OSX, XP and Ubuntu on different drives (both the XP and the Ubuntu share a drive with other data I use in OSX).

I've installed rEFit, and when it is launched, I get the option to boot into any of the 3 OS's.  However, every time I choose Ubuntu, it sends me to XP instead.

I've read this is an issue with rEFit, and I should install GRUB or LILO, but have only been able to find GRUB, and don't understand how to install it once I've downloaded it(it's a .deb file.... Debian?  and won't auto install in OSX).


So, the question of the day is how do I manage to select what OS I want to boot from once rEFit is launched and the options are presented?

---

### Post by cyberdork33 on 2009-01-19
> **jltnol said:**
> I've read this is an issue with rEFit, and I should install GRUB or LILO, but have only been able to find GRUB, and don't understand how to install it once I've downloaded it(it's a .deb file.... Debian?  and won't auto install in OSX).

You already have GRUB, I am sure. rEFIt is not a bootloader, you still need grub or lilo to boot Linux.

GRUB is installed by default with Ubuntu, so it is probably there already. There is an issue with Mac Pros and multiple disks though. Whichever disk you boot from is seen by the system as the primary hard drive (which is /dev/sda in Ubuntu) but when you installed it was likely seen as another disk (/dev/sdb or /dev/sdc), thus all the config files for grub probably point to the wrong location.

Also, Ubuntu is based on Debian and uses the debian package management system and binaries.

This infromation may be useful:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

---

### Post by jltnol on 2009-01-19
Thanks!

I had actually run across that link before but was still a bit confused... You've helped somewhat.. so what I'm guessing is that I need to log into Ubuntu, open GRUB, and edit the config file so it points in the correct direction, yes?

Assuming I can find GRUB, is the editing trivial, or will I need an advanced rocket science degree ?  <G>

Thanks again.

---

### Post by cyberdork33 on 2009-01-20
> **jltnol said:**
> Thanks!

I had actually run across that link before but was still a bit confused... You've helped somewhat.. so what I'm guessing is that I need to log into Ubuntu, open GRUB, and edit the config file so it points in the correct direction, yes?

Assuming I can find GRUB, is the editing trivial, or will I need an advanced rocket science degree ?  <G>

Thanks again.
file is /boot/grub/menu.lst

You will need to learn about GRUB's notation for hard drives:
[http://www.gnu.org/software/grub/manual/grub.html#Naming-convention](http://www.gnu.org/software/grub/manual/grub.html#Naming-convention)

---

### Post by nooBuntew on 2009-04-09
Sorry if this post is not completely Ubuntu specific, but this site seems to be one of the most active Mactel Linux forums available.  

So I just bought a new Nehelam 8-core Mac Pro, and I am looking to do a little bit of configuration testing.

I have outfitted my new machine with 4 drives that have a total of 8 TB of disk space.  What I am hoping to do is to put 4 partitions on each disk at ~500 GB apiece and then load up the entire machine with a mix of the following old and new OS's if possible:

Mac OS X (Leopard)
Windows Vista
Windows HPC Server 2008
Windows 7 Beta
Ubuntu 8.04
Ubuntu 8.10 or later
Fedora 10
Fedora 5 or 6
RHEL 4.3
RHEL 5
SuSE 9.3
SuSE 10.0 or 11.0

and possibly one or two other flavors of Linux for good measure.  The main purpose of all this mess of operating systems is for product testing purposes, but also to avoid the use of a virtual machine and run an operating system directly on the hardware (primarily because of an MPI application that may or may not play well with the virtual machine).

After a few days of trial and error, I have realized that if I want to have all of the Windows installs visible, they needed to be among the 4 visible partitions on the first hard drive (the EFI partition being the 1st visible on /dev/sda1, with OSX ending up /dev/sda5).  I have also installed rEFIt within OSX in order to select an operating system at startup.

With the first drive in place, I then moved on to the second drive.  On this drive, I have initially installed Fedora 10 on one ext3 partition and I set up one swap partition, leaving the rest as free space.  I could easily take one of the other disks and do something similar with Ubuntu as a first step.

When I place both hard disks in my MacPro and start the system (where the only EFI partition is on the Windows disk), rEFIt boots up and I see the Apple icon (for OSX), 3 Windows icons (for Vista, HPC, 7), and one Tux (for Fedora).  

When I attempt to select Tux, the Windows Boot Manager then appears, which means I cannot boot into Linux.

So my question is the following:

Is there any way that I can configure my machine such that I will be able to boot all 3 versions of Windows, and at least 1 version of Linux (but preferably every one in that list above)?

I am open to suggestions and will be spending quite some time in the days or weeks ahead trying to get this to work.

---

### Post by cyberdork33 on 2009-04-10
The Mac has an odd way of designating what the primary drive is when the system is running. It seems to be able to change this depending on how it is booted. I think is your problem with booting Linux. There is not a whole lot of detail available, but there is a note here that should help:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

Be aware also that if you are booting linux via bios-compatibility-mode (the way windows is booted, and most linux distros would use by default, in fact, i don't know of any that don't), that grub has to be installed on one of the first four partitions, and, the /boot (or / if not using a separate /boot) partition has to be one of the first four partitions. This is because grub depends on the bios compatibility, and the bios compatibility can only handle 4 partitions in it's table. swap, /home, or whatever else can safely be beyond #4 as once the Linux kernel is loaded, it is capable of reading the real GUID Partition Table (GPT) and mount those partitions. I wrote an article on this you may be interested in:
[http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/](http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/)

There is also the need to make sure that the GPT and MBR Partition Tables are in sync. You can easily sync the tables on the first drive with the partition tool in the rEFIt menu. For other drives, you can use 'gptsync' in the Ubuntu repos. 

You also have the option of trying to boot most of those Linux installs via EFI with grub-efi. This will simplify your partitioning issues. There has been a lot of work recently on getting it working well for this task. See the thread here:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

