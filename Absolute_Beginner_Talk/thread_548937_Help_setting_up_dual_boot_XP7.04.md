---
title: "Help setting up dual boot XP/7.04"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by hessblake on 2007-09-11
Today I installed Ubuntu. My computer has 2 hard drives, a 200gb IDE drive, and an 80gb SATA drive.  I already had XP installed on to the 200gb, and wanted to install Ubuntu onto the 80gb.  So I told the partitioner to automatically partition the entire 80gb drive.  I can boot into Ubuntu only if I use the boot selection on my motherboard, and I cannot boot into XP anymore, but the files are still on the drive.  

Any help?

---

### Post by rsambuca on 2007-09-11
Don't worry, we should be able to fix this.  From ubuntu, could you post the outputs of the following commands?  To open the terminal, go to your top menu bar and select "Applications -> Accessories -> Terminal"

```
cat /boot/grub/device.map
``````
cat /boot/grub/menu.lst
```and ```
cat /etc/fstab
```

EDIT:  and 

sudo fdisk -l

---

### Post by mikewhatever on 2007-09-11
From Ubuntu Applications>Accessories>Terminal, can you post the output of the following > cat /boot/grub/menu.lst

---

### Post by hessblake on 2007-09-11
blake@blake-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/hdc
(hd1)   /dev/sda

blake@blake-desktop:~$ cat /boot/grub/menu.lst
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
timeout         3

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
# kopt=root=UUID=c6c3f727-4d7a-461d-a003-0be516d050fe ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c6c3f727-4d7a-461d-a003-0be516d050fe ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c6c3f727-4d7a-461d-a003-0be516d050fe ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


blake@blake-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c6c3f727-4d7a-461d-a003-0be516d050fe /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7401a86f-b6cc-4b79-b39c-083fcec4b8b2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by rsambuca on 2007-09-11
You will want to add the Windows entry to the ubuntu grub menu.lst to give you the option of booting either system.  To do this, open the file in the gedit text editor by entering the following command in a terminal:```
gksudo gedit /boot/grub/menu.lst
```To the very bottom of the grub, add the following lines so it looks like this:```

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 
root (hd0,0)
makeactive
chainloader +1
```
then save the file and reboot.  You should have the option of booting to either ubuntu or windows

---

### Post by hessblake on 2007-09-11
Thanks for the help, but I cannot boot into Windows.  Windows shows up on the bootloader, but when i hit enter, it says "NTLDR cannot be found, press CTRL + ALT + DEL to restart"

---

### Post by rsambuca on 2007-09-11
What do you have for the boot order in your bios.

---

### Post by Trevo_Teh_Nerd on 2007-09-11
Might he have to change that to hd1,1?

Edit: nevermind I just remembered he had two hard drives...

---

