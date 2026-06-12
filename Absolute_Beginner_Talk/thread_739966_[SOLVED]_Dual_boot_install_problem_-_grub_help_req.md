---
title: "[SOLVED] Dual boot install problem - grub help required"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by emptybox on 2008-03-30
I tried to install Ubuntu 7.10 as a dual boot with XP Home on to a computer with two hard drives.
The XP is on the master hard drive hd0, and Ubuntu is on the slave hd1.

I installed from the live cd, and used guided install, and just chose which hard drive to install Ubuntu to. It didn't ask me anything about grub.

The install seemed to go OK, but when I start the PC now, all i get is

grub stage 1.5
Error 21

It doesn't give me any choices, and won't allow me to boot into either XP or Ubuntu.
If I press Ctrl+Alt+Del it starts up the Dell loading screen (it's a Dell PC), but then just goes back to grub error 21?

I can boot into the Ubuntu live CD, and can see the two disks, and the files for both XP and Ubuntu are present and correct on their respective disks.

I'm hoping that someone can help me fix grub so I can boot into both OSs.
I don't mind reinstalling Ubuntu, but I hope to avoid the need to reinstall XP.

Here is the result of fdisk-l from the live cd
............................................................................

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa55ea55e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d9217e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9824    78911248+  83  Linux
/dev/sdb2            9825       10011     1502077+   5  Extended
/dev/sdb5            9825       10011     1502046   82  Linux swap / Solaris

Disk /dev/sdc: 252 MB, 252182528 bytes
16 heads, 32 sectors/track, 962 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x1570fe52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         962      246256    6  FAT16
ubuntu@ubuntu:~$ 
.......................................................................................................

And here is the result of /boot/grub/menu.lst from the installed Linux
......................................................................................
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
# kopt=root=UUID=43e4623f-83d0-4a53-8847-e0e61aff1ba4 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=43e4623f-83d0-4a53-8847-e0e61aff1ba4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=43e4623f-83d0-4a53-8847-e0e61aff1ba4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
.................................................................................................................

I see the Ubuntu enties are present, but it hasn't added an entry for Windows XP.
I also see that  **groot=(hd1,0)** , which I think means it's put the grub on the secondary disk.
Not sure if that's where it's supposed to be?

Any help gratefully received. :)

---

### Post by Jose Catre-Vandis on 2008-03-30
Look here

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

---

### Post by Moop on 2008-03-30
You probably just need to change the hdd you boot from. Go into the bios setup and change it to boot from the Ubuntu hdd. To boot windows add to grub:
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

---

### Post by emptybox on 2008-03-30
> **Moop said:**
> You probably just need to change the hdd you boot from. Go into the bios setup and change it to boot from the Ubuntu hdd. To boot windows add to grub:
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

Is that without changing the physical jumpers on the hard drives?
Just change  the Bios to boot from the slave?

---

### Post by emptybox on 2008-03-30
Anyway, thanks very much. :)

Changing the Bios seems to have done the trick, and I have added Windows XP into the grub list.
I'll see if I can mark this as solved.

I'll almost certainly have other problems, as I've got an ATI graphics card, but that's for future questions. :)

---

