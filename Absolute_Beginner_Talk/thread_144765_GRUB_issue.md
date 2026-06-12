---
title: "GRUB issue"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by gdoyel on 2006-03-15
I'm new to ubuntu, new to linux, but not necessarily new to computers in general.

I have installed Ubuntu fine, as a dual-boot with WindowsXP. I love Ubuntu, but still have to keep WinXP until I figure out how to get some of my Windows program essentials on Linux. 

I can get into Ubuntu fresh off the install, but after shutting down or rebooting to switch into WinXP, my computer will turn on and then say that GRUB is loading, and reboot.

And it does this ad infinitum.

Any help is appreciated.

---

### Post by Koybe on 2006-03-15
I'm not sure I understand. Are you still able to get into ubuntu or is it Windows you can't.

If you can access ubuntu, go, open a terminal and give us informations such as :
```
sudo fdisk -l
sudo cat /boot/grub/menu.lst
```

If you can acces only windows, i guess you'll need to boot on a live cd to get grub installed correctly.

---

### Post by incubus on 2006-03-15
Can you hit ESC in GRUB so that you can choose something?

Sounds like you have to reinstall/reconfigure GRUB. I would boot a Live Distro CD or a new Ubuntu ISO if you have access to that.

In what order did you install windows and linux?

incubus

---

### Post by gdoyel on 2006-03-15
To answer the questions, I installed WinXP first and then Ubuntu.

When I reboot, I cannot log into either ubuntu or windows, and have to reinstall ubuntu to be able to do anything.

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6670    53576743+   7  HPFS/NTFS
/dev/sda2   *        6671        7266     4787370   83  Linux
/dev/sda3            7267        7296      240975    5  Extended
/dev/sda5            7267        7296      240943+  82  Linux swap / Solaris

-----------------------------

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by meborc on 2006-03-15
i guess you have to install grub again... [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

---

### Post by gdoyel on 2006-03-15
A bit of an update. When I try to boot into Windows, it runs a CHKDSK and says its deleting something and then fixing it.

I can only assume that this is GRUB, as after I reboot, I can't do anything.

---

