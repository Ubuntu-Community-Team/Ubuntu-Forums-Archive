---
title: "dual booting PclinuxOS and Ubuntu"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by whabo on 2007-11-25
I need help with dualbooting those 2 Oses i had ubuntu FIrst, but then Ran the LiveCd for PclinuxOS .. partitioned my Hard drive and installed it on the new partition. However when i restarted ..  it took me straight to PclinusOS .. Grub did not give me a menu or a list of OS available.. so i again i grabbed Ubuntu's live CD and reinstalled Ubuntu's grub .. but now i cant see PclinuxOs's  partition in the menu it takes me straight to Ubuntu... Help ANyone? thx for reading this. 

PS i searched on teh forums for GRUb recovery and followed the instructions to get ubuntu booting. but i do need PclinuxOS partition as i think it runs faster on my PC. but ubuntu has a bigger packaged software collection .deb .. thx ...

---

### Post by Ub1476 on 2007-11-25
Post your grub menu file:

```
sudo gedit /boot/grub/menu.lst

```

---

### Post by whabo on 2007-11-25
> **Ub1476 said:**
> Post your grub menu file:

```
sudo gedit /boot/grub/menu.lst

```

This is what i get .. thx for your help... so what do i do next?? .. im sry but i a complete nub .... :S 

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
# kopt=root=UUID=7f5c3169-f926-44f1-bc5a-794e396e943d ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7f5c3169-f926-44f1-bc5a-794e396e943d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7f5c3169-f926-44f1-bc5a-794e396e943d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Ub1476 on 2007-11-25
If you see at the bottom it only contains Ubuntu, which means you will have to add PCLinuxOS to it. Since Ubuntu is on hd 0,0 I guess PCLinuxOS is on hd 0,1.

So, add this to your grub menu:

```
title: PCLinuxOS
root: (hd0,1)
makeactive
chainloader +1
```

Here's an example for you:

```
## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7f5c3169-f926-44f1-bc5a-794e396e943d ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7f5c3169-f926-44f1-bc5a-794e396e943d ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title: PCLinuxOS
root: (hd0,1)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by louieb on 2007-11-25
> **Ub1476 said:**
> If you see at the bottom it only contains Ubuntu, which means you will have to add PCLinuxOS to it. Since Ubuntu is on hd 0,0 I guess PCLinuxOS is on hd 0,1.

So, add this to your grub menu:

```
title: PCLinuxOS
root: (hd0,1)
makeactive
chainloader +1
```

That will work if you installed PClinuxOS GRUB pointer in the boot sector of its partition. IF not then this should. [COLOR=DarkOrange]**May have to adjust (hd#,#)**[/COLOR] to fit your installation. 
```
title Linux Distro 2 on /dev/sda2
  configfile (hd0,1)/boot/grub/menu.lst
```[Nuts on Grub]("http://louboldt.com/ilinuxgrub.htm")

---

### Post by GavinZac on 2007-11-25
why not try running one or the other in a virtual machine?

---

### Post by whabo on 2008-01-15
i do thank you for your help .. im sorry for teh delay .. i havent been on forums for a while.

---

### Post by Omnios on 2008-01-15
Counting on your install pertaining to Grub. It will look for grub files on the last os you installed grub on. So if you installed grub on Pclinux the grub loader infor will be there.

---

