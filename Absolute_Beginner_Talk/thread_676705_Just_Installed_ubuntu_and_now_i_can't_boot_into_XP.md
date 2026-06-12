---
title: "Just Installed ubuntu and now i can't boot into XP home"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by roachkazy on 2008-01-24
fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11eb11eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21244   170642398+   7  HPFS/NTFS
/dev/sda2           21245       38728   140440230   83  Linux
/dev/sda3           38729       38913     1486012+   5  Extended
/dev/sda5           38729       38913     1485981   82  Linux swap / Solaris


menu.lst

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=28a4c06b-f3ff-45dc-b013-115fe6533769 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=28a4c06b-f3ff-45dc-b013-115fe6533769 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=28a4c06b-f3ff-45dc-b013-115fe6533769 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

please help, i love linux

---

### Post by LaRoza on 2008-01-24
I don't know why it doesn't work. 

Try booting Windows with the Super Grub Disk, see the link in my sig. If all else fails, you can reinstall the Windows bootloader. 

This doesn't fix the problem, but will allow you to get into Windows. 

If you ever need to reinstall Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sirzepp on 2008-01-24
I've used the windows repair console and the command "FIXMBR" to repair the windows boot-loader, then reinstall GRUB when stuff like this happens.  If you aren't up to burning the GRUB DISK then you just need to load up the windows installation disk and select the repair console, enter the number for your install(there is a menu) and enter you administrator password(possibly just hit enter at the prompt...if you never entered an administrator password).  The Grud disk is probably a better way, but if your windows disk is just sitting there, you can restore the windows bootloader that way.

---

### Post by LaRoza on 2008-01-24
> **sirzepp said:**
> I've used the windows repair console and the command "FIXMBR" to repair the windows boot-loader, then reinstall GRUB when stuff like this happens.  If you aren't up to burning the GRUB DISK then you just need to load up the windows installation disk and select the repair console, enter the number for your install(there is a menu) and enter you administrator password(possibly just hit enter at the prompt...if you never entered an administrator password).  The Grud disk is probably a better way, but if your windows disk is just sitting there, you can restore the windows bootloader that way.

The Super Grub Disk can also be used to boot Windows, without touching the hard disk. 

@OP Follow the advice with the Windows disk, if you have it. SGD is small, though, so if you have a blank disk on hand, you might want it anyway.

---

### Post by roachkazy on 2008-01-24
Wow you are amazing, however i have now tried the super grub and no luck. i am going to give the XP disc a shot but i am a little confused.

1: c:/windows

is what comes up when i boot into the cd

do i hit "1 and then enter"

after do i type?

"fixmdr"

this might be a bad post because i am going to give it a shot now.

thank you all very much

---

### Post by sirzepp on 2008-01-24
> **roachkazy said:**
> Wow you are amazing, however i have now tried the super grub and no luck. i am going to give the XP disc a shot but i am a little confused.

1: c:/windows

is what comes up when i boot into the cd

do i hit "1 and then enter"

after do i type?

"fixmdr"

this might be a bad post because i am going to give it a shot now.

thank you all very much

You'll hit '1' and then enter your administrator password(possibly just hit enter at that prompt, if you never entered a password for administrator)

Then, I think you type, "FIXMBR"
if that doesn't work, then type help and it will list the commands available.

Look for one that says "FIXMBR" OR something like it...and type that.  I'm pretty sure it's FIXMBR(I just did this a couple of nights ago)...but I can't remember.

After that it will ask you if you want to re-write the boot sector, say yes, and after it's done, type exit

After that the machine will reboot and it should boot directly into windows(you've just written over GRUB, so you won't get a menu).  If you want to get GRUB back after that, I'm not sure what to do.  I've only done this when I wanted to delete linux and start over...and GRUB gets installed when I install a new distro.

---

### Post by roachkazy on 2008-01-24
i tried and i failed

i tried the fixbrm with no luck

now i have to boot into linux with the grub super which kinda of sucks

i think what is wrong is that when i installed linux it asked me where i wanted to put it and i said in the most continues space or the first option. the problem with that is when i installed XP i partitioned the drive to give it less room. IE 100GB drive and i only gave XP 20GB leave the linux a whole 80GB. so what i think i did was install it on the 20GB part and not the 80GB where i wanted to put it.

does any one think this might be right?

i am still trying to fix this so let me know if you have any more ideas and thanks again for all you help.

---

### Post by backflip on 2008-01-24
> **roachkazy said:**
> i tried and i failed

i tried the fixbrm with no luck

now i have to boot into linux with the grub super which kinda of sucks

i think what is wrong is that when i installed linux it asked me where i wanted to put it and i said in the most continues space or the first option. the problem with that is when i installed XP i partitioned the drive to give it less room. IE 100GB drive and i only gave XP 20GB leave the linux a whole 80GB. so what i think i did was install it on the 20GB part and not the 80GB where i wanted to put it.

does any one think this might be right?

i am still trying to fix this so let me know if you have any more ideas and thanks again for all you help.

When it happened to me fixboot, then fixmbr worked.

---

### Post by sirzepp on 2008-01-24
I totally forgot about fixboot...I think that might be the issue.  I once had to use both of those commands when my machine simply would not boot windows...and it worked.  I agree...try the windows CD again and run fixboot and then fixmbr.

---

### Post by roachkazy on 2008-01-25
Thanks you people of the net, i will try now.

---

### Post by roachkazy on 2008-01-26
well all failed and now i am reinstalling once again. but here is a new problem. blue screen. says to check for viruses? man this is becoming to much.

any suggestions?

---

