---
title: "GRUB occasionally stops working"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by wilywampa on 2008-01-06
I have Ubuntu 7.10 installed to dual boot with Vista on my laptop.  I completely regret installing Ubuntu at this point, because it had several problems including wireless not working and the display not working properly.  I mostly regret installing Ubuntu because the GRUB bootloader decides to stop working every few reboots so my computer just reboots to the POST message repeatedly.  To fix the problem, I have to completely reinstall Ubuntu to get GRUB to fix itself.  It there an easier way to fix GRUB?  I can't just intall the Vista bootloader because my laptop didn't come with a Vista install disc, only a recovery disc which is useless.

Thanks in advance.

---

### Post by eternicode on 2008-01-06
You can reinstall GRUB without reinstalling Ubuntu.  You can normally do it from within an Ubuntu installation, but in your case it sounds like you'll have to boot to a LiveCD.  Ubuntu's livecd will work.

In a terminal, do:

```

$ grub

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu
.lst"... succeeded
Done.

grub> quit

```

Your results for "find /boot/grub/menu.lst" will probably be different, make sure to use the correct (hdX,X) notation.

That sequence should do the trick in reinstalling grub, but your "corrupt grub" situation is strange.  Could you post your /boot/grub/menu.lst file (from your Ubuntu installation)?  Perhaps we can find out what's causing grub issues.

---

### Post by philinux on 2008-01-06
> **wilywampa said:**
> I have Ubuntu 7.10 installed to dual boot with Vistaon my laptop.  I completely regret installing Ubuntu at this point, because it had several problems including wireless not working and the display not working properly.  I mostly regret installing Ubuntu because the GRUB bootloader decides to stop working every few reboots so my computer just reboots to the POST message repeatedly.  To fix the problem, I have to completely reinstall Ubuntu to get GRUB to fix itself.  It there an easier way to fix GRUB?  I can't just intall the Vista bootloader because my laptop didn't come with a Vista install disc, only a recovery disc which is useless.

Thanks in advance.

what's the POST message. Could be a hardware problem? Any beeps.

---

### Post by wilywampa on 2008-01-06
Here is my menu.lst:

```
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
# kopt=root=UUID=214c1b51-9acc-4d36-a563-3e065a6dc4af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=214c1b51-9acc-4d36-a563-3e065a6dc4af ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=214c1b51-9acc-4d36-a563-3e065a6dc4af ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Here is what happens when I attempt to do what you told me to do:

```
grub> find /boot/grub/stage1

Error 15: File not found

grub> find /boot/grub/menu.lst

Error 15: File not found

grub> find /media/disk/boot/grub/stage1

Error 15: File not found

grub> root (hd0,5)

Error 21: Selected disk does not exist

grub> root (hd0,0)

Error 21: Selected disk does not exist

```

Thanks for the help, though.

---

