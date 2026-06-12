---
title: "boot sequence problem"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by benner on 2007-03-24
when edgy was running i had no trouble but i just took a chance and dumped it for a fresh install of feisty.  now, when i boot, i have to enter the setup and manually select which drive to boot from.  it doesn't save and i have to do it again each time.  the motherboard is made by a company called 'spark' and supports socket 939/socket 754 processors.  the chipset is nvidia (i think) and i have an amd 4200+ dual core, asus vidoe card with ati x550 chipset (256mb).  when i boot, there's various RAID stuff coming up that i don't understand.  when i enter raid setup, i have no idea what to do so i leave it alone.  the bios boot setup boot sequence only lists 'cd-rom' 'hard disk' etc... but has nothing for more than one hard disk.  when i enter the special 'boot menu' (by hitting esc) it lists various options.  i select 'hard disk' and it opens another menu where i can select from the 2 drives and it boots just fine.  when i restart, i have to do it all over again.  if i just let it go by itself, it gives me an error message (error 15: file not found) and to press any key to continue, which of course doesn't help.  when i hit 'esc' a little later in the process, to enter the grub menu, i can see the linux kernel, recovery mode and so on but whichever i select, it doesn't work.  when i installed it this morning, i wanted to resize my hard disk and install into a new partition.  the partition manager crashed each time i tried, i ran a gparted disk to try to resize that way and couldn't.  it would give me an error and revert back to the way it was.  i finally gave up and told it to erase everything and reinstall.  there wasn't anything important on there anyways.  any suggestions?  i know i have a lot i should learn about here but in the meantime, it is a drag to have to restart this way each time.  thanks in advance...

the disks are hdb1 and sda1.  the one with the OS is sda1.  i only have one operating system.  no dual boot.

---

### Post by sad_iq on 2007-03-24
Could you paste the menu of grub here? (sudo gedit /boot/grub/menu.lst) ...let's see if something can be done!!!

---

### Post by benner on 2007-03-24
here it is...

(thanks for the quick response)

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
# kopt=root=UUID=ff3830fd-def7-41ec-95cc-5fea04e33423 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=ff3830fd-def7-41ec-95cc-5fea04e33423 ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=ff3830fd-def7-41ec-95cc-5fea04e33423 ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by benner on 2007-03-24
i posted as requested...  i'm reading everything i can about grub in the meantime.  hard to follow.

---

### Post by benner on 2007-03-24
i figured it out in case this is useful to any other new folks...

i just changed (hd1,0) to (hd0,0) each time it appeared.  just a guess, but it worked.

there is a 'super grub disk' that i read about.  i burned it and ran it but it wasn't something you could figure out as you went along.  it needed some additional reading to understand how to use it.

---

