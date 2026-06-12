---
title: "Booting from USB hard drive"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by sleepytom on 2006-12-08
I've installed Ubuntu Dapper onto a USB hard drive with a machine running Windows XP on the internal hard drive, but I cannot seem to boot Ubuntu. I let the installer partition my USB drive as it saw fit.

It seems Grub did not notice the Windows OS on the internal drive, and does not give me the a selection of boot choices. My bios does allow a setting to boot from the USB HDD, so I sequence the boot attempts as follows: CD, USB HDD, Internal hard drive. But the USB HDD boot always fails, and the sequence passes on to the Windows boot from the internal drive.

Any ideas on how to gett the OS to load? ](*,)

---

### Post by msn4us on 2006-12-08
post ur menu.lst  u will find it in

 ```
/boot/grub/menu.lst
```

maybe u need to modified it:-k

---

### Post by sleepytom on 2006-12-08
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by msn4us on 2006-12-08
if u had one partition in ur usb hdd u must change 

```
(hd0,0)
```

to

```
(hd1,0)
```

that if u had the boot-looder grub in ur main hard drive 


2- also u can press F2 or F12 or Delete and select from bios USB stronge

that all i know:-k

---

### Post by sleepytom on 2006-12-08
Unfortunately, I cannot edit this file becuase:
- I can't boot into my installed Ubuntu
- When I try to save it from the Live CD, I get an error that I don't have permission to write to that file.

If I change the boot sequence in my bios to boot only from the USB-HDD, then I get an error that states something like "Boot error, please insert boot disk."

Bummer. I'd really like to get this going.

---

### Post by bodhi.zazen on 2006-12-08
> **sleepytom said:**
> 
- When I try to save it from the Live CD, I get an error that I don't have permission to write to that file.

LOL

boot the live CD

mount the usb drive


use sudo to give you write permission:

```
sudo gedit /path/to/menu.lst
```

Save and exit

Reboot

---

