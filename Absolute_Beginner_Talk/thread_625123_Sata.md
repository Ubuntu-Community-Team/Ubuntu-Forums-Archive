---
title: "Sata ?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by squiggs on 2007-11-27
Does UBuntu work out of the box with SATA drives? I've just managed to get Windows back, after trying to install Linux Mint. GRUB error or something to that effect. Any advice on how Promise Fastrack S150 Controller operates with Ubuntu. My machine is a DELL Dimension 8600. From looking at these threads, i'm assuming a bit of tinkering is required?

[http://ubuntuforums.org/showthread.php?t=580756](http://ubuntuforums.org/showthread.php?t=580756)
[http://ubuntuforums.org/showthread.php?t=591288](http://ubuntuforums.org/showthread.php?t=591288)
[http://ubuntuforums.org/showthread.php?t=492114](http://ubuntuforums.org/showthread.php?t=492114)

---

### Post by Taboo Mirage on 2007-11-27
SATA drives will work out of the box.

---

### Post by Dr Small on 2007-11-27
Both of my Sata Drives worked out of the box.

---

### Post by squiggs on 2007-11-28
Guys I've went ahead and installed Linux to the Hard disk. I get the same errors as with Mint - Grub Error 2. I've attempted to fix my Windows Partition with the Windows CD - 

fixboot c:
fixmbr


I now get an Operating System not found error or something along those lines. Any help appreciated. I'm determined to get this to work - I've spent too much time on it to give up now!

Thanks in advance guys,

---

### Post by squiggs on 2007-11-28
I've now managed to at least restore the Grub error. I think perhaps my Grub menu.lst is wrong, I'd like to experiment with changing hd0 to hd1 etc.. is this on the right lines? I think what may be happening is that there is a utility partition on my machine (Dell Dimension 8600) - and that Linux cannot load from this. How can I edit files when Im using the Live CD? Do I have to mount the drive or something?

---

### Post by Dr Small on 2007-11-28
NTLDR is not found ?
Well, from past expirence, you can not have two SATA hard drives plugged in when installing Windows. We kept getting the `NTLDR is not found` error because of it (on my Dad's system). So, maybe that has something to do with it...

Dr Small

---

### Post by Dr Small on 2007-11-28
> **squiggs said:**
> I've now managed to at least restore the Grub error. I think perhaps my Grub menu.lst is wrong, I'd like to experiment with changing hd0 to hd1 etc.. is this on the right lines? I think what may be happening is that there is a utility partition on my machine (Dell Dimension 8600) - and that Linux cannot load from this. How can I edit files when Im using the Live CD? Do I have to mount the drive or something?
Yes, you must mount the drive, browse to /boot/grub/menu.lst and edit the file directly there.

Dr Small

---

### Post by squiggs on 2007-11-28
Thanks for the quick reply..How do I go about mounting it? 

mount sda

?----


tried this...

ubuntu@ubuntu:/dev$ mount sda
mount: can't find sda in /etc/fstab or /etc/mtab
ubuntu@ubuntu:/dev$ mount sda1
mount: can't find sda1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:/dev$ mount sda2
mount: can't find sda2 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:/dev$ sudo mount sda
mount: can't find sda in /etc/fstab or /etc/mtab
ubuntu@ubuntu:/dev$

---

### Post by Dr Small on 2007-11-28
If you are running the Ubuntu LiveCD, then open Nautilus, and you should see your drive on the left side. Right click it, select mount, then open it.

---

### Post by squiggs on 2007-11-29
Ok Ive mounted SDA now...please see menu.lst for Grub. I also tried unplugging one of the disk in the SATA configuration - and just installing on one. No juice. Same Grub Error. I also have downloaded the Super Grub Disk if anyone has any commands I can try with it.


 menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=a874f76e-8356-4a08-b43c-524b4c433277 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a874f76e-8356-4a08-b43c-524b4c433277 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a874f76e-8356-4a08-b43c-524b4c433277 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by squiggs on 2007-11-29
*bump*

---

