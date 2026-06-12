---
title: "Why won't my Windows partition mount?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-04-01
Here is the contents of my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1799fb0e-faef-4d28-90d9-89f89f08cd79 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=1218E18618E16965	/media/sda2	ntfs	defaults,umask=007,gid=46	0	1
# /dev/sda6
UUID=8232-4442  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=c00f4dcf-0799-4ccf-a083-7b7fe296d37f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

What I'm really aiming to do is get Ubuntu to recognize my windows partition at /dev/sda2, then get it into GRUB somehow (I have no idea how to do that) so that when I boot, I can select my OS of choice.

---

### Post by artfwo on 2008-04-01
Most likely, it's marked as "dirty" (perhaps, after being incorrectly unmounted). Did you try to run chkdsk for it from Windows? If you don't have windows, you can also try setting the **force** mount option to mount it (despite being unchecked):

```
UUID=1218E18618E16965	/media/sda2	ntfs	defaults,**force,**umask=007,gid=46	0	1
```

---

### Post by talsemgeest on 2008-04-01
To add an operating system into the grub, you add it to your menu.lst: ```
gksudo gedit /boot/grub/menu.lst
```
Here is my one just in case you need an example: ```
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/black-hole-ws.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=87d34352-4799-4170-a107-a2967d23f548 ro

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
# defoptions=splash vga=791

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=87d34352-4799-4170-a107-a2967d23f548 ro splash vga=791
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=87d34352-4799-4170-a107-a2967d23f548 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title         "Microsoft Windows"
root         (hd0,1)
makeactive
savedefault
chainloader      +1 
```

Hope this helps :)

---

