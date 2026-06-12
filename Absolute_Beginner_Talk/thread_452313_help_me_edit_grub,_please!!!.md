---
title: "help me edit grub, please!!!"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by benner on 2007-05-23
i am running ubuntu 64 feisty in sda1 and just installed kubuntu 32 feisty in sda4.  i keep downloads in sda3.  they are all on a single SATA hard disk.   i also have another hard drive that is hdb1.  i originally installed it all with the extra hard disk removed.  grub kept getting screwed up and i got an error (15 or 22 i think it was) so i removed it, installed ubuntu64 in sda1 and edubuntu 32 in sda4.  then i connected the other hard drive (IDE) and all was fine.  edubuntu had a melt down.  i still wanted a 32 bit OS so i installed kubuntu over it.  now i am having the grub problem again and i don't want to reinstall again.  here is my current grub menu:

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
# kopt=root=UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(sda1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(sda1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(sda1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by renzokuken on 2007-05-23
im confused as to what you want to do exactly

---

### Post by benner on 2007-05-23
when i reboot, i get an error.  i see the grub menu but no matter what i select, i get an error.  not found.

---

### Post by benner on 2007-05-23
please!  someone!  

the exact error is 

"error 22, no such partition"

so now the only thing i can do is boot from a live cd.

---

### Post by rillip on 2007-05-23
Are these actually installed on sda1 as the menu says?  Or are they on a different partition?  To be clear, this is the first partiotion on your first sata drive, though which one is first can be a bit tricky, as the bios/Linux/Windows might choose three different orders.

You might try running 

sudo apt-get update 
sudo apt-get upgrade

To install the latest kernel, ans the ones listed are oldish.

---

### Post by benner on 2007-05-23
i can't boot into it.  i guess that the bios is looking in the wrong place for the kernel.  when i installed kubuntu it edited grub and now the machine can't find it.  i would like to edit grub so that it points to the right place.  but i don't know what to change.  when i look in gparted (from the live cd) i see my ide drive (no OS, just data) listed as hdb and then i see all 3 partitions on sda (1,3 and 4 plus swaps).  i see kernel files and grub files and grub menus in sda1 and sda4.  how do make the bios find them?

---

### Post by benner on 2007-05-23
i got it (sort of...)

my guess is that when i installed a second os in a new partition and it edited grub, it put it on the other hard disk.  so it was looking on the wrong drive.  something like that anyways because when i went into the bios setup and switched it to boot from the other disk, i was able to get it to work.  it still did a weird thing where i got an error saying that apt-get wasn't installed and then a command prompt as root.  i hit ctl+alt+del and it suddenly booted into the system properly.  i will have to figure out what that is all about but at least i got into my system.  thanks, folks.

---

