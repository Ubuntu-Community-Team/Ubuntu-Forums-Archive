---
title: "Dual booting Xp and Feisty(2 Harddrives)"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Znort_Ubern00b on 2007-12-05
Ok, here is my query.

I have feisty installed on my pc, i also have an XP hard drive from another pc. I want to install that harddrive and be able to dual boot...

this thread says its easier to boot and change bios boot order.
[http://ubuntuforums.org/showthread.php?t=630908&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=630908&highlight=dual+boot")
which i dont want to do as it just seems laborious to do every time.

What i want to know is how can i set it up so as i get an option when i boot up. I am fairly new to all of this so step by step guide would be appreciated.

Regards
Znort

---

### Post by saulysw on 2007-12-05
Znort,

Well, I came at this from a slightly different angle myself. I had a drive with XP, then added a second drive which I wiped and added Ubuntu. Doing it this way around, the installer detected the XP drive and added it as an option to the GRUB loader. Now when I boot, it gives me the choice of XP or Ubuntu. There is no BIOS changing involved. Also, if my second drive dies the old XP drive will boot happily by iteself, like it originally did. I tested this by disconnecting the Ubuntu/GRUB drive. 

Now, if you have Ubuntu already and add a drive with XP, I'm not sure what will happen exactly. I know it's possible to configure GRUB to load other OS's on other drives, so perhaps that's what you need to research. I'm sorry, I'm not an expert in this area but I was hoping my comments might help. My suggestion really is to just try it and see. Watch out for the whole master/slave thing on the IDE drives, which is done with jumpers on the drive itself. 

Good luck!
- Saul

---

### Post by shafin on 2007-12-05
First,see what drive is primary and which one is secondary,then install grub.
Then edit /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```

Then compare this menu.lst with your one and take necessary changes
The red lines are not part of the file
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0[COLOR=Red](set the default operating system here,XP or ubuntu)[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,9)/boot/grub/splashimages/Blu.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3d486e29-da12-4151-b886-52ca5cc7044e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)

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
# defoptions=quiet splash vga=791

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

[COLOR=Red](This is for Gutsy)[/COLOR]## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,9)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3d486e29-da12-4151-b886-52ca5cc7044e ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,9)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3d486e29-da12-4151-b886-52ca5cc7044e ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,9)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[COLOR=Red](This one is for Vista)[/COLOR]title        Windows Vista
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```

Here comes the tricky part.The primary hard disk is hd0,the secondary one is hd1.Thus if your ubuntu system resides at the first partition of the primary HDD,it should have [COLOR=Red]root        (hd0,0),[COLOR=Black]for the second HDD,it will be[/COLOR] [/COLOR][COLOR=Red]root        (hd1,0),[/COLOR][COLOR=Red] [COLOR=Black]and if the operating systems are at partitions other than the first one,change it accordingly,for instance,if your ubuntu partition lies at the 3rd partition of the 2nd hdd,its entry will be[/COLOR] [/COLOR][COLOR=Red]root        (hd1,2).[COLOR=Black]
Hope its clear,you can first install GparteED and connect the XP drive,that way,you'll see the [/COLOR][/COLOR][COLOR=Red](hdx,x) [COLOR=Black]names of the partitions from GpartEd and be sure.[/COLOR][/COLOR]

---

### Post by gn2 on 2007-12-05
If you can access a "Boot Device Selection Menu"  by pressing F8, F2 or whatever key at boot then you may be able to select which drive to boot from that way.

The hard drive from the other PC will probably not boot in the new PC without doing a "Repair Install" from the relevant XP CD.

---

### Post by ukripper on 2007-12-05
Make backup first!!!!!!before you do anything

Then do Installation. If grubs get corrupted then use super grub disk to restore or use above Grub installation using live cd.

You would need gparted from live cd to make partitions if needed.

---

