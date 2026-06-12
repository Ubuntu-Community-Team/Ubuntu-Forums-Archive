---
title: "Update Changes to Grub After Repartitioning"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by SVG64 on 2007-05-10
Hi, all. When I first installed Ubuntu, I installed Ubuntu on the 3rd partition after XP & Vista. But after re-partitioning (I decided to get rid of Vista), the name of the mount points have changed. I think my XP mount is  now SDA1 and Ubuntu is SDA2. Problem is somewhere in the system it still remembers Ubuntu being on SDA3.

Occasionally after major updates, GRUB rewrites the whole menu.lst file and puts my "/" back on SDA3, and the only way I can boot back in is to boot up the LiveCD, mount the drive and manually edit GRUB.

While this is a little annoying, I really like to learn where GRUB stores the original partition information, can anyone give me pointers in this area? Thanks very much! :)

---

### Post by Bachstelze on 2007-05-10
In /boot/grub/menu.lst :

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
timeout         5

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

splashimage=(hd0,0)/grub/splash.xpm.gz

title           Gentoo GNU/Linux, kernel 2.6.21.1-ana-gentoo
root            (hd0,0)
kernel          /vmlinuz-2.6.21.1-ana-gentoo root=/dev/hda8 ro vga=0x318 video=vesafb:mtrr:3,ywrap
savedefault

title           Slackware GNU/Linux, kernel 2.6.21.1-ana-slack
root            (hd0,0)
kernel          /vmlinuz-2.6.21.1-ana-slack root=/dev/hda12 ro vga=0x318 video=vesafb:mtrr:3,ywrap
savedefault

title           Gentoo GNU/Linux, kernel 2.6.18.8-ana-gentoo
root            (hd0,0)
kernel          /vmlinuz-2.6.18.8-ana-gentoo root=/dev/hda8 ro vga=0x318 video=vesafb:mtrr:3,ywrap
savedefault

title           FreeBSD
root            (hd0,1,a)
kernel          /boot/loader
savedefault

title           Gentoo GNU/Linux, kernel 2.6.21/1-ana-gentoo (single-user mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.21.1-ana-gentoo root=/dev/hda8 ro single
savedefault

title           Debian GNU/Linux, kernel 2.6.18-4-686
root            (hd0,0)
kernel          /vmlinuz-2.6.18-4-686 root=/dev/hda12 ro vga=0x318 video=vesafb:mtrr:3,ywrap
initrd          /initrd.img-2.6.18-4-686
savedefault




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
# kopt=root=UUID=f5473f9c-8062-43a0-b65e-d237a17a1861 ro

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
# defoptions=

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
# altoptions=(single-user mode) single

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

```

The lines with only one # in front of them if the part of the file between the "AUTOMAGIC KERNEL LIST" are the default options, you can edit trhem to your needs.

---

### Post by SVG64 on 2007-05-11
Cool, thanks very much, HymmToLife! :popcorn:

---

