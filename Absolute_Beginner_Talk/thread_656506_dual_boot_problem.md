---
title: "dual boot problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-02
i have windows xp installed now, and i have restored grub, but when i turn on my computer it automatically boots into ubuntu, normally i would call this a good thing, but when i want to use something that only works with windows, it becomes a problem, how do I get a list at the startup that asks me if i want to boot in to xp or ubuntu?

---

### Post by thelatinist on 2008-01-02
Please post the results of:

```
cat /boot/grub/menu.lst
```

---

### Post by meborc on 2008-01-02
ok... do you have a hidden grub menu? or will it flash by too quickly? you should (by default) be prompted to choose between ubuntu and other OS'es for 10 seconds before the boot continues...

for some grub versions, you have to hit esc-key to see the menu

to change the menu find the menu.lst file in /boot/grub/ 

it is quite self explanatory, you can change the settings for how long the menu is shown and what is the default selection etc etc... just be sure to make a copy of the file before editing!!!

---

### Post by antisocialist on 2008-01-02
> **thelatinist said:**
> Please post the results of:

```
cat /boot/grub/menu.lst
```

```
allan@allan-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=2fcb45cc-3753-4f00-abfe-d6135bdb97af ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2fcb45cc-3753-4f00-abfe-d6135bdb97af ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2fcb45cc-3753-4f00-abfe-d6135bdb97af ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=2fcb45cc-3753-4f00-abfe-d6135bdb97af ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=2fcb45cc-3753-4f00-abfe-d6135bdb97af ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by antisocialist on 2008-01-02
> **meborc said:**
> ok... do you have a hidden grub menu? or will it flash by too quickly? you should (by default) be prompted to choose between ubuntu and other OS'es for 10 seconds before the boot continues...

to first and second sentences:
how should i know
to third sentence:
i know i should be, the problem is that i am not, that is why i asked, im not trying to be a drill person, who makes sure everybody knows their stuff :p

---

### Post by thelatinist on 2008-01-02
Do the following:

1) Backup your menu.lst file by doing:

```
sudo cp /boot/grub/menu.lst boot/grub/menu.lst.bak
```

2) Open menu.lst for editing by doing:

```
gksudo gedit /boot/grub/menu.lst
```

3) Put a # before the line that reads hiddenmenu.

4) Save and exit.

5) Reboot.

---

### Post by antisocialist on 2008-01-02
nifty, it gives me 5 ubuntu options (2 dif kernels and recovery for each, and memtest) but there is no xp option, how do i add xp to the list?

---

### Post by jken146 on 2008-01-02
Please post the output of ```
sudo fdisk -l
```

---

### Post by antisocialist on 2008-01-02
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbab2bab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10701    85955751   83  Linux
/dev/sda2   *       10702       11976    10241437+   7  HPFS/NTFS
/dev/sda3           11977       12161     1486012+   5  Extended
/dev/sda5           11977       12161     1485981   82  Linux swap / Solaris

---

### Post by jken146 on 2008-01-02
> **antisocialist said:**
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbab2bab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10701    85955751   83  Linux
/dev/sda2   *       10702       11976    10241437+   7  HPFS/NTFS
/dev/sda3           11977       12161     1486012+   5  Extended
/dev/sda5           11977       12161     1485981   82  Linux swap / Solaris

Thanks.  This tells us that Windows is installed on sda2 (because it's formatted in NTFS).  So we need to add an entry in the Grub menu for the Windows bootloader, which should be on sda2.  The Grub equivalent for sda2 is (hd0,1).

Open up a terminal and type this: ```
gksudo gedit /boot/grub/menu.lst
```

Then paste the following at the end of the file:  ```
title		Windows
root		(hd0,1)
makeactive
chainloader	+1
```

Save the file, close the text editor and reboot.  You should now have a Windows option after all the Ubuntu options.

---

### Post by antisocialist on 2008-01-02
is there a way i can hide 3 of the options (i only want the 2 kernel option ones) but not delete them from the list?

---

### Post by jken146 on 2008-01-02
You can comment them out (put a # in front of each line in the entry).  That way they'll still be in the file, but not read bu Grub.

I recommend that you keep recovery mode -- it may well save you a bit of bother.

---

### Post by antisocialist on 2008-01-02
cool

---

