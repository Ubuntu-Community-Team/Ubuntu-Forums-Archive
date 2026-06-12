---
title: "Removing grub"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by cesiel1990 on 2006-12-26
Does anyone know how to remove grub using a Ubuntu live disc instead of a Windows disc?  If so how?

---

### Post by dwblas on 2006-12-26
You do not want to remove Grub.  You want to replace it with something else as it is what boots the os.  If you want only Windohs for example, then installing Windohs will replace grub with the Windohs boot manager.  If you want to do something like use LILO instead of grub, installing LILO will replace grub.  Once you have a new boot manager installed you can use Synaptic to remove grub.

---

### Post by bulldog on 2006-12-26
> **cesiel1990 said:**
> Does anyone know how to remove grub using a Ubuntu live disc instead of a Windows disc?  If so how?

I assume you won't be using ubuntu anymore? because if you remove grub you can't boot it anymore.

Okay,you can use a cd called Rescue cd and you can find it here,

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

Do some reading and you'll find out how it works.

---

### Post by cesiel1990 on 2006-12-26
I was having a boot problem while using GRUB and was trying to get rid of it so I could at least get into windows, and I figured that out.  Now it seems that when I install Ubuntu it does not automatically install GRUB like that past versions I have used (Even though it should) and is booting straight to windows when I restart. Does anyone know how I easily setup GRUB with the live cd manually?

---

### Post by bulldog on 2006-12-26
A little drastic to reinstall when you have troubles with GRUB,don't you think?:D 
You can manipulate GRUB very easy FYI.
To install GRUB with the live cd to the MBR of (hd0) you can choose another one if you like.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by cesiel1990 on 2006-12-26
I've tried that, but when I start the computer GRUB never shows and it boots straight into windows.

---

### Post by bulldog on 2006-12-26
Have you more than one hard disk?
Can you give me the output of ```
sudo fdisk -l (l as in like)
```

If you boot the live cd and we mount your ubuntu partition,can you give me your menu.lst?
To make a mount point```
sudo mkdir /mnt/rescue
```
To mount ```
sudo mount /dev/??? /mnt/rescue
```
To access the menu.lst```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

I can fill the question marks if I have the fdisk output.

---

### Post by cesiel1990 on 2006-12-26
fstab:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17592   141307708+   7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6884    55295698+   7  HPFS/NTFS
/dev/sdb2            6885        8937    16490722+  83  Linux
/dev/sdb3            8938        9039      819315   82  Linux swap / Solaris

Disk /dev/sdc: 512 MB, 512753664 bytes
56 heads, 32 sectors/track, 558 cylinders
Units = cylinders of 1792 * 512 = 917504 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         559      500592    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(838, 55, 32) logical=(558, 39, 32)

```

menu.lst:
```
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c8995864-8c7a-4a1b-b2b4-bb73afa4f3ea ro
# kopt_2_6=root=/dev/sdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

---

### Post by cesiel1990 on 2006-12-26
I'm still trying to figure this out anyone have a suggestion?

---

### Post by dwblas on 2006-12-26
I have a suggestion, but I'm not sure.  I think you want setup(sd0) instead of setup (hd0).  I can't look any deeper right now, but would think that "grub sata" entered into Google would confirm or deny this suggestion.

---

