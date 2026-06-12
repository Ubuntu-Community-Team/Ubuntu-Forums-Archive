---
title: "dual boot xp restarts"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by tcrosby86 on 2007-07-19
I searched the forum and couldnt find my exact problem so..........

i installed ubuntu on my comp a couple days ago using the live disc, the installion went fine, and ubuntu runs great, but i tried to run windows xp today and it said starting up... and it showed the windows screen with the loading bar then instantly restarted...... i tried to load xp again and same thing happens over and over. i have no clue where my windows xp disc is what can i do to get this thing working again?

---

### Post by loserboy on 2007-07-19
did you defrag windows before you installed ubuntu?

you could try starting xp in safe mode or last known good

---

### Post by rillip on 2007-07-19
Resizing the partition is always risky, but few run into issues with it.  Sounds like you might have bad luck.  Without an XP disk I can only recommend what loserboy did.  I believe it will prompt you right after it says "Verifying DMI" to hit F8 or such to choose options on how to boot.  I'd try safe mode, but once you're in safe mode, I don't know what you'd do to fix it without a Windows disk.  I'd probably recommend finding one and running the windos repair program from the disk, or reinstall.

---

### Post by kilkraze on 2007-07-19
You could try a system restore once you are in safe mode. Click no at the window that appears once you are in safe mode. Restore the system to a previous state.
Why am I discussing windows in a ubuntu forum?

---

### Post by asmoore82 on 2007-07-19
post the contents of the Windows section of your GRUB config (/boot/grub/menu.lst)

---

### Post by tcrosby86 on 2007-07-19
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
# kopt=root=UUID=3033d251-e6fb-4194-9e9f-73a36632138c ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3033d251-e6fb-4194-9e9f-73a36632138c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3033d251-e6fb-4194-9e9f-73a36632138c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3033d251-e6fb-4194-9e9f-73a36632138c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3033d251-e6fb-4194-9e9f-73a36632138c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by tcrosby86 on 2007-07-19
safe mode restarts it as well.....

---

### Post by loserboy on 2007-07-19
well this is over my head, but if you go to the wondows boot options again and do safe mode with command you should be able to see the file it hangs on.... problem is I wouldnt know what to do after that.

have you had any recent power outages or improper shutdowns

---

### Post by tcrosby86 on 2007-07-19
I tryed all forms of booting windows, but all do the same.... my cousin is maioling me his xp disc..... so i guess i can fix it some how when it gets here.

---

### Post by asmoore82 on 2007-07-20
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1 **<==WARNING: Winders is installed on Secondary Master IDE Drive**
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

how many hard drives are in your computer and why are you not running OSes off of the Primary Master?

---

