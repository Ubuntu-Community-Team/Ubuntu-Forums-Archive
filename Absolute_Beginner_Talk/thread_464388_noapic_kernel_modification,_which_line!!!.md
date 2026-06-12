---
title: "noapic kernel modification, which line!?!?!"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Grundalizer on 2007-06-04
ive had this bug 8254 timer not connected to apic, i read you can get rid of this by changing the kernel.  i did sudo gedit /boot/grub/menu.lst

i came up with

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
# kopt=root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

my question is, do i put noapic after the "no splash" under end default options or under default options

---

### Post by Cypher on 2007-06-04
Yes, add the "noapic" option after the "ro quiet splash" on the first entry. So it should go from:
```

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```
to
```

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro quiet splash **noapic**
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

---

### Post by Grundalizer on 2007-06-04
awesome i love you

---

### Post by Cypher on 2007-06-04
Wow..uhh..thanks..I..think..:p

---

### Post by Grundalizer on 2007-06-04
ok so i hit save after i added noapic.  then i heard i had to run update-grub  is that correct?

i did 

```
god@Gods-laptop:~$ update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
cp: cannot remove `/boot/grub/menu.lst~': Permission denied
god@Gods-laptop:~$ 


```

how can i make sure it is permanent fix now?

i just used sudo update-grub and it worked!!!!!!   when in doubt, use sudo, i am learning. thank you for fast reply and help!

---

### Post by Cypher on 2007-06-04
You don't really want to run 'update-grub' as it creates a new 'menu.lst' file by looking at the /boot direcotry. So you should go back and check to see if your "noapic" option is still there or gone.

When GRUB loads on power-up, it will read your 'menu.lst' file from the HD and do the appropriate thing. Back in the days of LILO, after a change to its configuration file, you had to run '/sbin/lilo' to update the static config. GRUB doesn't need that last step.

---

### Post by Grundalizer on 2007-06-05
I do sudo gedit /boot/grub/menu.lst

add "noapic" to the end of the first kernel line after splash, hit save, and open it up again and the noapic part is not on there, how do i get it to stay?

---

### Post by mckooiker on 2007-11-27
> **Grundalizer said:**
> I do sudo gedit /boot/grub/menu.lst

add "noapic" to the end of the first kernel line after splash, hit save, and open it up again and the noapic part is not on there, how do i get it to stay?

Maybe a bit late, but I hope this will help somebody.....
Are you installing ubuntu with Wubi? If so, probably you have to change the menu.lst that you can find in windows (somewhere in c:/wubi/.....)
Cheers,
Maarten

---

