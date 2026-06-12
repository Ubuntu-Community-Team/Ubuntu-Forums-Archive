---
title: "GRUB Menu problem, maybe"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by straigle on 2008-02-16
Ok, I think I messed up.  I deleted lines from the grub menu, older kernels and such.  After I did this windows seemed to not boot.  But it wasn't that it booted randomly, it took a set amount of times before it would boot ok.

It seems to be something with the grub/boot parameters, although I know for a fact I only deleted older (linux kernel 2.16.20, etc.).

It's that it takes windows a pretty consistent amount of times to actually boot, that makes me believe it to be some sort of simple grub fix?  Any takers?

/boot/grub/menu.lst
>  # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=da22c7bd-0c19-4e0a-a4c4-18b5dfd96b37 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=da22c7bd-0c19-4e0a-a4c4-18b5dfd96b37 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=da22c7bd-0c19-4e0a-a4c4-18b5dfd96b37 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=da22c7bd-0c19-4e0a-a4c4-18b5dfd96b37 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=da22c7bd-0c19-4e0a-a4c4-18b5dfd96b37 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

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





My original post about the subject:

>  First time poster, so obviously I have never had any major problems on my dual-boot machine. Love the forums and never had to post cause my questions had been answered, until now.

I've dual booted for the past two years, no problems. Well, I hadn't booted up Ubuntu recently due to vacation and a major move. I had 133 updates ready to install. Installed them, then followed the guidelines on another post to clean up the system (autoclean, autoremove, synaptic stuff, etc.) everything seemed to be working fine, internet, etc. I clean up my grub by only deleting the reference lines to older kernels, no biggie there either.

Well I reboot my comp everything still looks fine, but when I try and boot Windows it goes to black screen, then reboots again. Every now and again it boots, but nothing works. Not internet, programs barely load, but it's really random when it will actually boot up. I checked some posts on the forum about GRUB menu stuff, still to no avail.

Well I boot up ubuntu just to make sure it is in working order, and it is, except, network/internet is also down on it. I figure the two are related, but this is the first time I've been stumped about where to start. Any help would be greatly appreciated.

Edit: Tried to boot from an XP CD, acted the same as trying to boot from Windows, but I can boot from it. It just sometimes does not boot and just reboots instantly.

Edit: While trying to load XP CD, it automatically restarted during the process.

Edit: Problems must not be related. Was able to fix network card by disconnecting, reconnecting and restarting. Boot problems persist though. Random boot patterns will not boot Windows every time.

---

### Post by kyphi on 2008-02-16
There should be a backup copy of your menu.lst file in boot/grub.  Make a duplicate, temporarily rename the current menu.lst file to menu1.lst and rename the duplicate backup file menu.lst.

Then reboot and see if XP boots as expected.

---

### Post by dstew on 2008-02-16
It seems to me that your Windows menu entry might not be correct. The grub root is listed as (hd0,0), but the title says /dev/hdc1. Usually, grub (hd0,0) equals /dev/sda1 (grub counts from zero).

Let's see what your partitions look like. Post the output of the command```
sudo fdisk -l
```

---

