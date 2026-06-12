---
title: "Have Vista, installed Ubuntu 7.04 , no more Vista?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by bodean on 2007-04-19
Have Vista on my laptop. Created a partition, installed ubuntu, now when the bootloader comes up, and I select Vista, it reboots the computer. There is no way for me to boot up in Vista. Help

---

### Post by n3tfury on 2007-04-19
hopefully you didn't resize the Vista partition while installing Ubuntu?

> After the installation of Windows Vista, you will want to install Linux. DO NOT resize the Vista partition during the installation of the Linux distribution! Due to the change in NTFS versions, no Linux partitioning program, nor standard Windows partitioning programs, can properly alter the partition that Vista is installed to.

[http://www.pro-networks.org/forum/about78184.html#dualboot](http://www.pro-networks.org/forum/about78184.html#dualboot)

---

### Post by bodean on 2007-04-19
> **n3tfury said:**
> hopefully you didn't resize the Vista partition while installing Ubuntu?



[http://www.pro-networks.org/forum/about78184.html#dualboot](http://www.pro-networks.org/forum/about78184.html#dualboot)

No, it was done, then rebooted, then installed ubuntu.

Says I need to edit menu.lst
How do I do this? I tried opening it with text editor, but wouldnt let me edit/save it

---

### Post by KIAaze on 2007-04-20
> Says I need to edit menu.lst
How do I do this? I tried opening it with text editor, but wouldnt let me edit/save it

You have to open it with superuser privileges in order to save changes.
Do:
```
sudo gedit /boot/grub/menu.lst
```
(you can of course replace gedit with your favourite editor (nano, pico, kate, emacs...))

However, I don't know how to edit it to solve your problem...

---

### Post by confused57 on 2007-04-20
> **bodean said:**
> No, it was done, then rebooted, then installed ubuntu.

Says I need to edit menu.lst
How do I do this? I tried opening it with text editor, but wouldnt let me edit/save it

Here's how to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

If you can't get Vista booted, post the output of your menu.lst and:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by bodean on 2007-04-20
> **confused57 said:**
> Here's how to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

If you can't get Vista booted, post the output of your menu.lst and:
```
sudo fdisk -l
```
the -l is a small "L"

Thanks.  I'll give it a try.  This is what my menu.lst looks like ::

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
# kopt=root=UUID=8e71e05f-1e50-43be-81a0-a16f50de6269 ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8e71e05f-1e50-43be-81a0-a16f50de6269 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8e71e05f-1e50-43be-81a0-a16f50de6269 ro single
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
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title         "Windows Vista"
root         (hd0,0)
chainloader      +1

---

### Post by docshawnc on 2007-04-20
Back up the file and then try removing these lines at the end of it:

title "Windows Vista"
root (hd0,0)
chainloader +1

---

### Post by bodean on 2007-04-20
Same problem happening. Computer just restarts, back to OS load menu.

What will the fdisk command do that you posted?

---

### Post by docshawnc on 2007-04-20
fdisk -l lists the partitions on your drive

---

### Post by bodean on 2007-04-20
Thanks. Where do you want me to run "sudo fdisk -l" at? I run it in terminal within ubuntu, and the command doesn't work.

---

### Post by jvc26 on 2007-04-20
```
sudo fdisk -l
```is run in the terminal window in ubuntu.
Il

---

### Post by Happy_Man on 2007-04-20
Applications --> Accessories --> Terminal

---

### Post by az on 2007-04-20
> **bodean said:**
> Have Vista on my laptop. Created a partition, installed ubuntu, now when the bootloader comes up, and I select Vista, it reboots the computer. There is no way for me to boot up in Vista. Help

[http://ubuntuforums.org/showpost.php?p=2490978&postcount=5](http://ubuntuforums.org/showpost.php?p=2490978&postcount=5)

Can you use the vista disk and repair the bootloader?

---

### Post by bodean on 2007-04-20
> **az said:**
> [http://ubuntuforums.org/showpost.php?p=2490978&postcount=5](http://ubuntuforums.org/showpost.php?p=2490978&postcount=5)

Can you use the vista disk and repair the bootloader?

I will not know til Saturday night when I return home from my trip.  Was trying to fix it out on the road..

---

### Post by confused57 on 2007-04-20
> **bodean said:**
> Thanks. Where do you want me to run "sudo fdisk -l" at? I run it in terminal within ubuntu, and the command doesn't work.

Run the command in a terminal:
```
sudo fdisk -l
```
the -l is a small "L"

---

