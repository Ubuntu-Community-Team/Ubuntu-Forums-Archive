---
title: "Dual Boot"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by drulated on 2007-05-01
First time user - installed ubuntu 7.04 successfully but cannot get into windowsXP. At installation step the system recognised that I had just one hard drive and partioned 66% to windowsXP (96+GB) with the remainder being set up for Linux. I assume that the MBR has been corrupted, but how? and can it be fixed?

---

### Post by lw5 on 2007-05-01
Please post your /boot/grub/menu.lst file

---

### Post by notwen on 2007-05-01
Did your install replace MBR w/ Grub?  Upon rebooting you should be getting prompted by Grub to select an OS and give you 10ish seconds to select it before starting the default OS(Typically your new Ubuntu install).  Should have something along these lines in Grub.

1. Linux
2. Linux (recover mode)
3.Linux (memtest)

Other Operating Systems:
Windows XXX

---

### Post by Ozeuss on 2007-05-01
Does GRUB load ok? does it show the "windows xp" option? (it should list the kernels you have, then a memtest option, and the "other operating systems".
post your /boot/grub/menu.lst file, and the output of "sudo fdisk -l" from terminal, so that people will have a clearer view.

---

### Post by drulated on 2007-05-01
I do get the options stated at startup. sorry I should have said that. When I select Windows XP the Windows screens appears momentarily  then loops back to the startup screen again. I have tried selecting WindowsXP then safe mode but again it gets so far then loops back , without displaying any message

---

### Post by alienexplorers on 2007-05-01
Please post your menu.lst by running "cat /boot/grub/menu.lst"

---

### Post by drulated on 2007-05-01
I'm so new to this - That I do not know were to enter the instruction - please advise

---

### Post by drulated on 2007-05-01
found where to enter the instruction - at last - sorry for the delay in answering your question




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
# kopt=root=UUID=a70791d5-28f7-45d9-8abb-7ea1c0d5d566 ro

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a70791d5-28f7-45d9-8abb-7ea1c0d5d566 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a70791d5-28f7-45d9-8abb-7ea1c0d5d566 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by drulated on 2007-05-01
Output from  - sudo fdisk -l        


Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         319     2562336   1b  Hidden W95 FAT32
/dev/hda2   *         320       12492    97779622+   7  HPFS/NTFS
/dev/hda3           12493       19620    57255660   83  Linux
/dev/hda4           19621       19929     2482042+   5  Extended
/dev/hda5           19621       19929     2482011   82  Linux swap / Solaris
sandy@sandy-desktop:~$

---

### Post by lw5 on 2007-05-01
So XP is on /dev/hda2? Then it looks like you need to toggle your boot flag (make it bootable) for that partition with fdisk..

---

### Post by drulated on 2007-05-01
Hi Iw5
           can you be more specific, Please. This all new to me.

Thanks for your help to date

---

### Post by drulated on 2007-05-03
Well either Ubuntu isn't ready for me or I'm not ready for it, which is a big disappointment.
Fortunately I had made an image copy of my hard drive before attempting to install UBUNTU 7.04 and was able to restore my hard drive (over 7 hours to complete) to a Windows XP system only.
Didn't give up at that, but tried again,but before installing UBUNTU 7.04 I inserted my winXP installation disc and when given the option choose the repair option and then at the prompt entered FIXMBR -just in case the problem was down to my installation.Then installed UBUNTU 7.04 but yet again it failed. Did a further restore and 7 hours later  thought I would try again, this time, using Partition Manager, I created Linux extension & swap area. UBUNTU 7.04 ignore this space and choose instead to use some 30% of the NTFS file. Despite trying I still cannot dual boot with Ubuntu 7.04 & Windows XP. I'll stick with Ubuntu only for the next few hours then do a complete restore (another long drearly 7 hours) Interestingly I cannot just insert my Windows XP and run FIXMBR to revert back to my XP system.

I'll keep checking the forum just in case some has had a similar experience and was able to overcome the problem

---

### Post by darren1270 on 2007-05-03
Wow that is a really long time....If there is nothing on the xp side that you really need.... The easiest way to do this is to simply re-install windows but you choose the partition size through windows set up and then install Ubuntu on the unused space... It will guide you through the steps... once you have your windows setup just boot from the live cd and install guided and you should be set... took me about 20 min from start to finish.

Good Luck!

---

### Post by drulated on 2007-05-03
Thanks darren for your suggestion, but over the years I have a wide variety of programs that I come to depend on, the installation of UBUNTU only took me about 20 mins but I'm afraid it would take a lot longer to reinstall Windows XP and all the programs I use, assuming I can find all the installation discs. Believe it or not that 7hours 9 mins to restore was for only 41GB and I had defrag the disc before making the image copy.

---

