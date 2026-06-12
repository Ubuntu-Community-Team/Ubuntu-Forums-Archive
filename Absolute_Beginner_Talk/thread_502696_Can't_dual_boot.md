---
title: "Can't dual boot"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by oldfart79 on 2007-07-16
I haven't been able to find a post exactly like my problem.  So here goes.

I downloaded the Ubuntu 7.04 desktop-i386.iso and burned it to CD.  I installed the OS, but when I rebooted I didn’t get a dual boot screen - instead went right into Windows.  I then downloaded bootpa26, unzipped and ran it.  I got the boot screen on the next reboot.

Please select the operating system to start:

	Microsoft Windows XP Home Edition
	Linux

Use the up and down keys to move the highlight to your choice.
Press ENTER to choose.


When I highlight the second line and hit enter, I get the following message.

BootPart 2.60 Bootsector © 1993-2005 Gilles Vollant [http://www.winimage.com/bo](http://www.winimage.com/bo)
otpart.htm
Loading new partition
Bootsector from C. H. Hochstatter
Cannot load from harddisk.
Insert Systemdisk and press any key.


I think my problem is that I don’t have a Linux boot partition for some reason.

The Gnome partition editor shows these drives:

/dev/sda1 	NTFS 			28.26 GB
/dev/sda3 	ext3 			26.08 GB
/dev/sda2 	extended 		57.44 GB
	/dev/sda5 	NTFS 		56.27 GB
	/dev/sda6 	linux-swap 	 1.17 GB


My System:
Abit IC7 motherboard
Phoenix Tech BIOS
Intel i875PE chipset
Intel Pentium 4 @ 3.2 MHz
1024 MB PC3200 @ 200 MHz DDR-SDRAM
Maxtor 120 GB ATA serial as C:\ drive w/WindowsXP SP2
60 GB partitioned (D:\ and E:\) parallel drive
Generic 56x CD-ROM
Pioneer DVR-109 DVD-RW
Gateway 24” LCD monitor, 1920x1200

Someone please help me.  I want to start using this great operating system.

---

### Post by Al3xK3aton on 2007-07-16
You need to put them on different partitions; Linux can't read NTFS.

---

### Post by oldfart79 on 2007-07-17
OK, I'm stupid.  Why can't Linux read NTFS?  I can see all my files (and open and edit them) when I boot into Feisty from the install disk.  Thanks for your quick reply, though.

---

### Post by NotRoot:-) on 2007-07-17
You are not stupid.  You are learning like all of us.  

Ubuntu's default configuration mounts NTFS Partions for Read Only.  I have seen projects for LInux to mount NTFS Partitions as Read/Write.  But I've never experimented with them.

Try the default installer for Ubuntu in the Live CD.  It should select the correct partition types.  It did that for me when I created a dual boot system by installing Ubuntu 6.10
on a Windows XP System. It installed GRUB as the boot loader to allow me to specify which OS to load during startup.

Ubuntu does mount a FAT Partition as read write.   I find that useful on my dual boot system.

---

### Post by oldfart79 on 2007-07-17
Thanks, notroot.  I'm a bit leery about trying to install again.  Do I have to somehow uninstall Feisty first?  Do I first have to erase the partitions that were added?

---

### Post by jvc26 on 2007-07-17
For your information, there is a great guide on dual booting here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Il

---

### Post by sailor2001 on 2007-07-17
> **oldfart79 said:**
> I haven't been able to find a post exactly like my problem.  So here goes.

I downloaded the Ubuntu 7.04 desktop-i386.iso and burned it to CD.  I installed the OS, but when I rebooted I didn’t get a dual boot screen - instead went right into Windows.  I then downloaded bootpa26, unzipped and ran it.  I got the boot screen on the next reboot.

Please select the operating system to start:

	Microsoft Windows XP Home Edition
	Linux

Use the up and down keys to move the highlight to your choice.
Press ENTER to choose.


When I highlight the second line and hit enter, I get the following message.

BootPart 2.60 Bootsector © 1993-2005 Gilles Vollant [http://www.winimage.com/bo](http://www.winimage.com/bo)
otpart.htm
Loading new partition
Bootsector from C. H. Hochstatter
Cannot load from harddisk.
Insert Systemdisk and press any key.


I think my problem is that I don’t have a Linux boot partition for some reason.

The Gnome partition editor shows these drives:

/dev/sda1 	NTFS 			28.26 GB
/dev/sda3 	ext3 			26.08 GB
/dev/sda2 	extended 		57.44 GB
	/dev/sda5 	NTFS 		56.27 GB
	/dev/sda6 	linux-swap 	 1.17 GB


My System:
Abit IC7 motherboard
Phoenix Tech BIOS
Intel i875PE chipset
Intel Pentium 4 @ 3.2 MHz
1024 MB PC3200 @ 200 MHz DDR-SDRAM
Maxtor 120 GB ATA serial as C:\ drive w/WindowsXP SP2
60 GB partitioned (D:\ and E:\) parallel drive
Generic 56x CD-ROM
Pioneer DVR-109 DVD-RW
Gateway 24” LCD monitor, 1920x1200

Someone please help me.  I want to start using this great operating system.

check your bios.....you should have booted direct into the cd-rom, which would have been the ubuntu live disk

---

### Post by dptxp on 2007-07-17
> **oldfart79 said:**
> Thanks, notroot.  I'm a bit leery about trying to install again.  Do I have to somehow uninstall Feisty first?  Do I first have to erase the partitions that were added?

No need to uninstall to reinstall. Only your / partition shall be formatted.

---

### Post by oldfart79 on 2007-07-17
Thanks, Illuvator and dptxp.  Your responses (as well as most of the others) helped lots.  I think I'm ready to redo it now.  Hope to be back soon with good news.

---

### Post by oldfart79 on 2007-07-17
Well, it's not good news.  I may now have a serious problem.  I reinstalled Ubuntu from the desktop CD and it looked like the installation was going well.  At the finishing prompt, I restarted (removing the CD).  Before I got to the dual boot screen, I got the (UGH!) message:  

Error loading operating system.

I dread to think I'm now screwed and must reinstall Windows, but I think that's my only option.  I can still get into the live CD, but will that help me?

Anybody got any good  ideas?

---

### Post by Kheldin on 2007-07-18
Don't panic. Unless you blew away your windows partition and/or formatted it, it's still there. More than likely your problem lies in Grub and a few simple corrections and everything will be booting fine again. Are you able to post your menu.lst from within /boot/grub ? Also the device.map file would be useful.

If not, can you highlight the Ubuntu OS choice as well as the XP choice and hit 'E' and post what is in there? Or is the grub boot menu not even coming up?

---

### Post by davidjmayo on 2007-07-18
Though this should not be necessary in a normal install, a complete cold boot (turn off pc, monitor etc, pull all plugs out, wait a minute) has been known to solve problems many times. It will clear out anything that may somehow of got left where it is

Give it a try  and see (no CD in the drive of course)

---

### Post by oldfart79 on 2007-07-18
Don't panic?  That's easy to say.  I'm not sure I'm doing this right.  Here goes with menu.lst first.  I copied the files to another networked working PC and opened them in Notebook, then copied the text here. I'm sure some of this can be edited out, but I don't know what's important, so I left everything in.  Hope you guys are not turned off.


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=03286ef4-865d-41a2-a133-2616f738903c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=03286ef4-865d-41a2-a133-2616f738903c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=03286ef4-865d-41a2-a133-2616f738903c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by Kheldin on 2007-07-18
When the Grub boot menu comes up, hit any key, then highlight your Windows XP entry and hit the 'E' key to edit it. Just try changing some of the numbers around and see if it will boot. That is:

title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

to

title Microsoft Windows XP Home Edition
**root (hd2,0)**
savedefault
makeactive
[B]map (hd0) (hd2)
map (hd2) (hd0)[/B]
chainloader +1

(Changes in bold) After you edit the entry, hit 'B' and try to boot it. If that doesn't work, try changing it to 0 (zero) instead.. (hd0,0), etc.. just mess with it and see if you can get into either Ubunut or XP. My setup is very similar to yours, and even though my device.map file is the same as yours, showing only 2 drives, using hd0 or hd1 doesn't work, I had to change it to hd2.. don't ask me why, but I'm sure it has something to do with a SATA drive as well as bios settings.

---

### Post by oldfart79 on 2007-07-18
Unfortunately, the boot sequence fails before the grub boot starts.  Does this mean that editing menu.lst will not help?  Should I try it anyway?  Could I make matters worse if I did so?

---

### Post by oldfart79 on 2007-07-18
Meanwhile, looked into editing menu.lst.  Can do only from the live cd.  Can't save edited file -- tells me it's read only.  How else can I do the edit?

---

### Post by Kheldin on 2007-07-18
Try switching to your other drive in BIOS to boot first.. see if that helps. If not, try changing:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

to

## default grub root device
## e.g. groot=(hd0,0)
**groot=(hd0,0)**

or

**groot=(hd1,0)**

or 

**groot=(hd2,0)**

and mess with the number combos.. eg- hd1,0 hd1,1 hd2,0 hd2,2 etc.. etc..

Just mess with the numbers until you see some progress. The reason I'm not real sure is because I think you re-installed and I'm not sure what device is what in your setup.

Grub installed somewhere, we just have to find it. One way is to know exactely everything that happened at install, and the other way is trial and error. :)

```
sudo gedit /boot/grub/menu.lst
```

should allow you to edit the file.

---

### Post by oldfart79 on 2007-07-18
I'm afraid I'm not making myself clear.  I CAN'T edit the menu/lst file.  I can get the computer up only from the live CD, and Ubuntu tells me that the files on the disk are read-only.  It won't let me save the edited file.  I hope there's another way.  Otherwise I'm stuck with a Windows reinstall -- which I hate to do.

---

### Post by catnappist on 2007-07-18
Just an observation from the peanut gallery.  I've never been able to do anything that required permission with the live CD.  Also, I'm real new at this, but it looks like linux is in the first partition and XP is in the next one.  Can that really work?  Last, seems like it would be a lot easier re-doing and formatting the partitions, reinstalling XP and then linux than trying to track down an error you might not be able to fix.

Luck.

---

### Post by Kheldin on 2007-07-18
Hmmm.. I'm not the most experienced with Grub, although I had the same kind of problems you are. Did you try switching the drive boot order in bios? If that still doesn't work, you shouldn't have to reinstall Windows. Just put your XP disc in, hit 'R' for the recovery console, and type 'fixboot'.. or is it 'fixmbr' ... can't remember.. you can do a 'fixboot /?' and 'fixmbr /?' from the recovery console and it will tell you what each does. Essentially, what they'll do is fix the Windows XP bootloader on the drive thus allowing you to boot into Windows again (without a reinstall).

I'm going to have to suggest if this is your first time attempting to dual boot a machine with Windows and a linux flavor, search for the many 'how-to' guides on this site as well as google. Sorry I don't have any links off the top of my head, but searching 'dual boot' in these forums will definitely point you in the right direction.

Sorry I couldn't be much more help. :(

---

### Post by oldfart79 on 2007-07-18
I appreciate everyone's kindness and prompt responses.  I know about fixboot and fixmbr on the recovery console.  My problem with them is, after I use either of them (preferably fixboot, as fixmbr is not supposed to be used with another OS on the hard drive), I'm not sure which partitions to delete so that I can reinstall Feisty.  Earlier advice to simply reinstall it without getting rid of the partitions an earlier install made got me into this fix in the first place.  Is there anyone out there who is watching and can help with this seemingly intractable problem?   I need to get back into WinXP so I can continue a project I've been working on for 15 years and I'm getting older every day.

---

### Post by oldfart79 on 2007-07-18
Well, people, I'm giving up.  I tried fixboot and fixmbr -- no help.  I erased what I thought were the Linux partitions, and lost one of my data drive parttions.  So I don't think Linux is ready for prime time yet, at least not in a dual boot configuration.  I've spent two precious days trying to get the system working.  Now I will have to spend two more days reinstalling Windows.  Too bad!  I learned a lot and liked participating in this forum.  Some day I'll be back, I'm sure.  Just not soon.  Thanks again.

---

