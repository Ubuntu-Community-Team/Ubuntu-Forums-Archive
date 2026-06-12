---
title: "help with GRUB bootloader"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-10
grub wont start therefore i cant run ubuntu(runs win xp pro)


help?

---

### Post by noynac on 2006-08-10
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29)

---

### Post by skale on 2006-08-10
If you have the live CD, boot it, mount your Ubuntu partition (if needed), and post the contents of /boot and the /boot/grub/menu.lst file.

---

### Post by L_o_N_e_R on 2006-08-10
Using the LiveCD and Overwriting the Windows bootloader

1. Pop in the Live CD, boot from it until you reach the desktop.

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).

3. Type "grub"

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

5. Type "setup (hd0)", ot whatever your harddisk nr is.

6. Quit grub by typing "quit".

7. Reboot. 


tried this wont work......

---

### Post by L_o_N_e_R on 2006-08-10
> **skale said:**
> If you have the live CD, boot it, mount your Ubuntu partition (if needed), and post the contents of /boot and the /boot/grub/menu.lst file.

this what your looking for?


drwxr-xr-x 2 root root 4096 2006-08-09 17:57 bin
drwxr-xr-x 3 root root 4096 2006-08-09 18:12 boot
lrwxrwxrwx 1 root root 11 2006-08-08 21:56 cdrom -> media/cdrom
drwxr-xr-x 4 root root 8192 2006-05-31 00:55 dev
drwxr-xr-x 106 root root 4096 2006-08-10 02:03 etc
drwxr-xr-x 3 root root 4096 2006-08-08 22:08 home
drwxr-xr-x 2 root root 4096 2006-05-31 00:49 initrd
lrwxrwxrwx 1 root root 29 2006-08-09 18:13 initrd.img -> boot/initrd.img-2.6.15-26-386
lrwxrwxrwx 1 root root 29 2006-08-08 21:57 initrd.img.old -> boot/initrd.img-2.6.15-23-386
drwxr-xr-x 19 root root 4096 2006-08-08 22:13 lib
drwxr-xr-x 2 root root 49152 2006-08-08 21:56 lost+found
drwxr-xr-x 5 root root 4096 2006-05-31 00:49 media
drwxr-xr-x 2 root root 4096 2006-05-22 14:00 mnt
drwxr-xr-x 3 root root 4096 2006-08-09 23:34 opt
drwxr-xr-x 2 root root 4096 2006-05-22 14:00 proc
drwxr-xr-x 7 root root 4096 2006-08-09 17:56 root
drwxr-xr-x 2 root root 8192 2006-08-09 18:06 sbin
drwxr-xr-x 2 root root 4096 2006-05-31 00:49 srv
drwxr-xr-x 2 root root 4096 2006-05-21 18:46 sys
drwxrwxrwt 6 root root 4096 2006-08-10 02:02 tmp
drwxr-xr-x 11 root root 4096 2006-05-31 00:51 usr
drwxr-xr-x 14 root root 4096 2006-05-31 01:02 var
lrwxrwxrwx 1 root root 26 2006-08-09 18:13 vmlinuz -> boot/vmlinuz-2.6.15-26-386
lrwxrwxrwx 1 root root 26 2006-08-08 21:57 vmlinuz.old -> boot/vmlinuz-2.6.15-23-386

---

### Post by 5-HT on 2006-08-10
> **L_o_N_e_R said:**
> 
tried this wont work......
What error messages are you getting on boot and when trying to reinstall GRUB? Does the computer boot straight into windows or do you receive a GRUB error?

In order to allow others to help, it would be nice to know a little bit about your setup. Do you have Ubuntu and XP on one hard drive or on separate ones? Which partitions are Ubuntu's (the root partition and /boot if it's separate are the most important) and which are for XP? As skale mentioned, could you post the contents of /boot/grub/menu.lst by using a live CD?

---

### Post by skale on 2006-08-10
Yep. now post the output of 
```
cat /boot/grub/menu.lst
```
Of course, make sure Grub is installed to the MBR, or master boot record (hda, hdb, sda, sdb) rather than the individual partitions (hda1).

Also the output of 
```
cat /etc/fstab
```.

---

### Post by L_o_N_e_R on 2006-08-10
> **skale said:**
> Yep. now post the output of 
```
cat /boot/grub/menu.lst
```
Of course, make sure Grub is installed to the MBR, or master boot record (hda, hdb, sda, sdb) rather than the individual partitions (hda1).

Also the output of 
```
cat /etc/fstab
```.



cat /boot/grub/menu.lst no such file or direcotry

---

### Post by Tomosaur on 2006-08-10
You will need to install Grub then.

---

### Post by L_o_N_e_R on 2006-08-10
> **Tomosaur said:**
> You will need to install Grub then.

and that would be how?

---

### Post by L_o_N_e_R on 2006-08-10
i tried doing this

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3)


now i need help on how to configure the grub menu...

---

### Post by L_o_N_e_R on 2006-08-10
so do i save this as menu.lst?

```
timeout 5 #The number of seconds GRUB should wait before booting an OS 
default 0 #The entry which should be booted by default
fallback 1 #The entry which should be booted in the event of the first one failing

title  Ubuntu, 2.6.10 #A 32-bit Ubuntu entry
#This (or something like it) should be in your configuration
root   (hd0,2)
initrd /initrd.img-2.6.10-5-386
kernel /vmlinuz-2.6.10-5-386 root=/dev/hda4

title  Ubuntu, 2.6.10 #Another 32-bit Ubuntu entry
#This is an example of an Ubuntu entry which does not have a separate /boot/ partition
#(it is provided only as an alternate to the example above -- do not use them together)
root   (hd0,2)
initrd /boot/initrd.img-2.6.10-5-386
kernel /boot/vmlinuz-2.6.10-5-386

title  Microsoft Windows XP Home #An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
makeactive
chainloader +1
```

(my boot is in /dev/hda4 so can any1 fix this for me if wrong ?)

---

### Post by L_o_N_e_R on 2006-08-10
bump

---

### Post by L_o_N_e_R on 2006-08-10
idk if this is useful 

this is the output from cat /boot/grub/menu.lst    from /dev/hda4

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda4 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           IBM WORKAREA
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by L_o_N_e_R on 2006-08-10
and of cat /etc/fstab```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by Tomosaur on 2006-08-10
Strange. It appears as if your menu.lst file is fine. Is it still the case that grub isn't working?

---

