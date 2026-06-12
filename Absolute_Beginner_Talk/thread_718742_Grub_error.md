---
title: "Grub error"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-03-08
Ive just re installed ubuntu on my sata HD now grub keeps bringing up errors and i cant boot ubuntu or windows on my other HD can anyone help?

---

### Post by taurus on 2008-03-08
What is the exact error message when you try to boot Ubuntu?

---

### Post by Tek-Noir on 2008-03-08
i think it was error 15 when trying to boot ubuntu off the sata and error 21 when trying to boot windows

---

### Post by corney91 on 2008-03-08
Has it not booted at all since you reinstalled? If so, your disc may be bad - check the CD integrity.
This happened to me once, it was GRUB boot error 15 or 16, I can't quite remember which.

---

### Post by Tek-Noir on 2008-03-08
The install was fine, i think all i need to do is sort grub out so it loads the OS

---

### Post by SloYerRoll on 2008-03-08
Do the following and post it here:

Open up a terminal and go to your grub directory:
```
cd /boot/grub
```
Then make a backup of your grub file in case things get crazy:
```
sudo cp menu.lst menu.lst_backup
```
Then open up your GRUB menu in gedit by doing the following:
```
gksudo gedit menu.lst
```

---

### Post by Tek-Noir on 2008-03-08
I cant cd /boot/grub cos im using the live cd at the min, i can cd to the grub menu on the first HD with ubuntu if you want?

---

### Post by SloYerRoll on 2008-03-08
> **Tek-Noir said:**
> I cant cd /boot/grub cos im using the live cd at the min, i can cd to the grub menu on the first HD with ubuntu if you want?No, that won't help. 

I'm not sure, but I know there's a way to get to your files on the HD and grab this configuration file. I guess you';; have to wait for someone more expercienced then me since I'm not sure  how to get there from the CD..:confused:

---

### Post by Tek-Noir on 2008-03-08
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
timeout		10

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
# kopt=root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro

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

title		Ubuntu, kernel 2.6.22-9-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro quiet splash
initrd		/boot/initrd.img-2.6.22-9-generic
quiet

title		Ubuntu, kernel 2.6.22-9-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro single
initrd		/boot/initrd.img-2.6.22-9-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



This is what i have in the menu.lst

---

### Post by taurus on 2008-03-08
How about?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by corney91 on 2008-03-08
> **Tek-Noir said:**
> I cant cd /boot/grub cos im using the live cd at the min, i can cd to the grub menu on the first HD with ubuntu if you want?
In the LiveCD, can you mount the filesystem? It should be in 'Computer'...

---

### Post by Fixman on 2008-03-08
Change the file to

> **Tek-Noir said:**
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		10

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
# kopt=root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro

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

title		Ubuntu, kernel 2.6.22-9-generic
root		(sd1,0)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro quiet splash
initrd		/boot/initrd.img-2.6.22-9-generic
quiet

title		Ubuntu, kernel 2.6.22-9-generic (recovery mode)
root		(sd1,0)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro single
initrd		/boot/initrd.img-2.6.22-9-generic

title		Ubuntu, memtest86+
root		(sd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(sd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by Tek-Noir on 2008-03-08
title Ubuntu, kernel 2.6.22-9-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-9-generic root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro quiet splash
initrd /boot/initrd.img-2.6.22-9-generic
quiet

title Ubuntu, kernel 2.6.22-9-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-9-generic root=UUID=cbaa2c40-25af-4c07-80df-77e5d9ec278b ro single
initrd /boot/initrd.img-2.6.22-9-generic

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

Im pretty sure i just need to change the numbers like (hd1,0) but i dont know what to

---

### Post by Tek-Noir on 2008-03-08
You sure that will work fixman? My ubuntu is on my sata and windows is on a seperate IDE

---

### Post by Tek-Noir on 2008-03-08
The grub device map is showing

(hd0)	/dev/hda
(hd1)	/dev/sda

Should it not be the other way around? ie.

(hd0)	/dev/sda
(hd1)	/dev/hda

---

### Post by Duck2006 on 2008-03-08
Post the output of,

sudo fdisk -a

as " taurus post asked"

---

### Post by Tek-Noir on 2008-03-08
Fixman I cant thank you enough! Sorted it right out. Thanks very much!

---

