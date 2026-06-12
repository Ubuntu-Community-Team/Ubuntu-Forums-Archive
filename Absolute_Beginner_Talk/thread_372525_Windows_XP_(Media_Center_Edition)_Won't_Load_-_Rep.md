---
title: "Windows XP (Media Center Edition) Won't Load - Repost"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by InsaneTuck on 2007-02-28
It would seem, due to a mixture of moronic wording (of course "Windows Media Center Won't Boot"...it's Linux, you hack!), and perhaps some poor timing, I had a bit of an issue that I desperately need addressed, but faded into the woodwork.  Stemp offered me a little help (Thank You, BTW), but I'm still without a solution, and the other posts up aren't seeming to help me.

Whenever I try to load WinXP, I am given a "Drive Error."  It then refuses to boot further, giving me one option: The three finger salute (CTRL-ALT-DEL).  Ubuntu is running fine...but since I live out where high-speed doesn't exist, I need Windows for my Internet access.  It also runs my editing programs...programs that make Wine scream and crash.

So, the following are all the bits I think are needed to fix this.  **First, my /boot/grub/menu.lst:**

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
# kopt=root=UUID=e2d42be9-c687-4073-87c3-5c4a67a17fc8 ro
# kopt_2_6=root=/dev/sda3 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

**Then, my drive structure:**

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30730 246838693+ 7 HPFS/NTFS
/dev/sda2 37764 38913 9230760 c W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3 30731 37474 54171180 83 Linux
/dev/sda4 37475 37763 2321392+ 5 Extended
/dev/sda5 37475 37763 2321361 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 4863 39062016 c W95 FAT32 (LBA)



I hope this is sufficient for one of you out there to offer me a solution...I've been a week without Windows, and my business is beginning to suffer...the local Public Access Station's editing equipment just isn't up to chops.

Thank you very much in advance...I'm eagerly looking forward to getting this fixed.

---

### Post by benfindlay on 2007-02-28
Hey, got a question about this bit first:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows NT/2000/XP
root (hd0,1)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

do you actually have all of these OSs installed (as in XP Pro, Media Centre and the NT/2000/XP one)? Either way, have you tried booting those relevant lines to see what they do?

---

### Post by benfindlay on 2007-02-28
Just had another thought: If you're desparate to get your windows partition back I believe you just need to boot off your XP disc, go to repair console and type ```
fixmbr
```

This will of course wipe-out grub and stop the ubuntu partition working, but as you say, the business is important. Then at least you could format the ubuntu drives and start again, hopefully it won't happen the 2nd time! ](*,) 

Hope this helps!

---

### Post by rsambuca on 2007-02-28
I agree with the fixmbr to get your XP back right away.  However, you won't have to re-format anything to get ubuntu back.  After you get XP running with the fixmbr, you can just re-install grub from the ubuntu liveCD.

A few other questions:  Was the rig ever booting properly?  If so, what caused it to stop working?

---

### Post by benfindlay on 2007-02-28
> After you get XP running with the fixmbr, you can just re-install grub from the ubuntu liveCD.


Very good point! Had forgotten that!

Also just spotted this in the grub config:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]
chainloader +1

I have never seen those 2 bold bits in my grub config before, and I may well be misreading it, but does it look to anyone like it is swapping the device locations of the 2 partitions around? May well do nothing, but its just a thought, am not familiar enough with the code and all to say so myself!

Hope this helps!

---

### Post by rsambuca on 2007-02-28
Windows only likes to preside in the primary drive.  The map commands fool Windows to thinking it is on the primary drive.

---

### Post by mahiyar on 2007-02-28
Exactly which windows do you want? Are all of them equally unacessable, as I see you have three XP's installed. There is another very important file the output of which is ignored, for grub there is no difference between SATA and PATA, so in case of multiple disks this file gives the association to GRUB, it is /boot/grub/device.map, go through it, are all your devices correctly mapped?

---

### Post by benfindlay on 2007-03-01
> **rsambuca said:**
> Windows only likes to preside in the primary drive.  The map commands fool Windows to thinking it is on the primary drive.

Thats pretty damn clever! Will have to remember that one!

---

### Post by InsaneTuck on 2007-03-02
First off, thank you all very much for the help - I appreciate this a lot.

First, on the question of the "Multiple Windows" - that was one that had me confused too. I in fact only have one version of Windows on my machine - XP Media Center. The other two do not actually exist. I don't know why Grub picked them up...perhaps by determining that, a clue as to how to manage running both at the same time will present itself.

Then, there's a new mystery that has occupied my time. Two out of these ethereal versions of Windows just report a "A disk error has occurred - Please press CTRL-ALT-DEL to Continue." However, I recently achieved an unespected result when I tried to access the third item - the one marked "Windows 2000/XP/NT." My computer is a HP Pavilion, and for whatever reason, it has detected something was wrong...when I entered this boot mode, the system activated the System Recovery Mode! I avoided the destructive restore, and went for the Windows Restore option.
Now the system won't enter Grub either. It simply reads the disk error message, and will not allow me to proceed. ](*,) 

Now, I do not consider this an issue, at least, not yet - this happened soon after running Ubuntu for the first time, and I was able to reactivate Ubuntu by reinstalling it and allowing Grub to restore. However, the fact that my system is behaving thus may offer a clue as to what the underlying cause is.

That, and benfindlay's bit of insight about the code appearing to refer back onto itself, which would likely cause an error, seems equally important. Excellent eye - I didn't even notice that.

In the meantime, I'll get my hands on an XP disk (I have the HP System Restore Disks...but I fear the system trying to run a destructive restore), I'll run fixmbr, and I'll keep you all posted. However, if we can figure out a way for my system to dual-boot properly, it would be, in the vernacular, "hella awesome." [-o<

---

### Post by Easy_Rider on 2007-03-02
first, if you boot your UBUNTU CD, you might be able to run the repair utility.. Try to do an install, but there should be a menu where you select repair, then you may be able to fix your grub loader that way.
SUSE cd1 has that capability, because I've used it a few times:)
here is my menu.lst, just for comparison( note the rootnoverify for the windows partition..):
cat menu.lst
# Modified by YaST2. Last modification on Thu Feb  8 23:54:46 UTC 2007
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.18.2-34-default root=/dev/sda6 vga=0x31a    resume=/dev/sda5 splash=silent showopts
    initrd /boot/initrd-2.6.18.2-34-default

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader (hd0,1)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.18.2-34-default root=/dev/sda6 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.18.2-34-default

---

