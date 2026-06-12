---
title: "[SOLVED] Kernel Help"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2007-12-24
At boot I get an error message for the Xen kernel, error 17 file not found  press enter to continue. When I hit enter a list of kernels pop up for me to choose from. They are as follows:

1. Xen-3.0 i386 2.6.19-4 generic
2. Ubuntu, Kernel lowletency 2.6.20-16 
3. Ubuntu, Kernel lowlatency 2.6.20-15generic
4. Ubuntu, Kernel lowlatency 2.6.20-15 (Recovery Mode)
5. Ubuntu, Kernel 2.6.20-16
6. Ubuntu, Kernel 2.6.20-15 generic
7. Ubuntu, 2.6.20-15(Recovery Mode)
8. Ubuntu memtest86+
9. Ubuntu Original

then, while booting I get : ata2.00: failed to set xfermode (err_mask=0x4) in 3 different spots

I tried loading the Zen kernel but got an error that Xgraphics and GPS wasn't configured correctly or something to that effect, then was taken to the do you want to configure blue screen. I don't know enough to continue so I tell it no then no again and am taken back to the boot screen then I have to shutdown manualy then restart and chose another kernel, the rest boot fine.

Can anyone help me with this?

---

### Post by tad1073 on 2007-12-26
Anyone? Is there anyone out there?

---

### Post by dstew on 2007-12-26
Boot one of your Ubuntu systems. Post the output of the following to the forum:```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by tad1073 on 2007-12-26
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password 
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password 
#      password 
# password 
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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

title           Xen 3.0-i386 / Ubuntu, kernel 2.6.19-4-generic
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /boot/xen-3.0-i386.gz
module          /wubi/boot/vmlinuz-2.6.19-4-generic find=/wubi/boot/linux ro console=tty0
module          /wubi/boot/initrd.img-2.6.19-4-generic
boot

title           Ubuntu, kernel 2.6.20-16-lowlatency
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-16-lowlatency find=/wubi/boot/linux ro quiet splash
initrd          /wubi/boot/initrd.img-2.6.20-16-lowlatency
boot

title           Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-16-lowlatency find=/wubi/boot/linux ro single
initrd          /wubi/boot/initrd.img-2.6.20-16-lowlatency

title           Ubuntu, kernel 2.6.20-16-generic
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash
initrd          /wubi/boot/initrd.img-2.6.20-16-generic
boot

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro single
initrd          /wubi/boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-lowlatency
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-15-lowlatency find=/wubi/boot/linux ro quiet splash
initrd          /wubi/boot/initrd.img-2.6.20-15-lowlatency
boot

title           Ubuntu, kernel 2.6.20-15-lowlatency (recovery mode)
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-15-lowlatency find=/wubi/boot/linux ro single
initrd          /wubi/boot/initrd.img-2.6.20-15-lowlatency

title           Ubuntu, kernel 2.6.20-15-generic
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd          /wubi/boot/initrd.img-2.6.20-15-generic
boot

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd          /wubi/boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.19-4-generic
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.19-4-generic find=/wubi/boot/linux ro quiet splash
initrd          /wubi/boot/initrd.img-2.6.19-4-generic
boot

title           Ubuntu, kernel 2.6.19-4-generic (recovery mode)
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /wubi/boot/vmlinuz-2.6.19-4-generic find=/wubi/boot/linux ro single
initrd          /wubi/boot/initrd.img-2.6.19-4-generic

title           Ubuntu, memtest86+
                find --set-root --ignore-floppies /wubi/boot/linux
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntustudio-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot

---

### Post by dstew on 2007-12-26
> kernel /boot/xen-3.0-i386.gzMaybe I don't understand what you are doing, but wouldn't the kernel line be kernel /wubi/boot/xen-3.0-i386.gz, based on where the other kernels are? But I don't know anything about this Xen distro really...

---

