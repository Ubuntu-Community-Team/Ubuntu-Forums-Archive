---
title: "Ubuntu  unistall,dual boot, 2HD's"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by normbob on 2006-10-30
Hello
 I had installed Ubuntu on my 2nd HD with  Windows XP on my first HD ( I did not disable my primary HD during install)
I would like to uninstall Ubuntu the easiest way possible.
I believe Grub is used

Is the Master boot record on the 2nd drive , there's a partition of 306 MB (logical drive)and also a partition of 6.2 GB

When I first boot the system there's a boot choice screen Ubuntu first then Windows. If it is not easy to remove Ubuntu I would like the choice of Windows first

Thank you
Normbob

---

### Post by blind0wl on 2006-10-31
Sounds like you have installed grub on the MBR of the first harddrive...or your primary master hard drive.  Which means your uninstall might be a bit difficult.

To change the default option on the menu, boot into Ubuntu and edit you /boot/grub/menu.lst

```
sudo nano /boot/grub/menu.lst
```

You will see as part of that file a setting that says 

```
## default num             
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
# 
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0   
```

You need to change the default 0, to the number of entries down in the file you have the windows selection, ie, heres my menu.lst

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default 3**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1e5d6f5b-f875-48c1-bab9-7747d99c2cde ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

[B]title Ubuntu, kernel 2.6.17-10-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1[/B]
```

Notice how I changed my default to 3?  Thats because starting from 0, my Windows XP is the 4th one down...0,1,2,3

Hope that helps

Blindy

---

### Post by normbob on 2006-11-01
Thanks Blindy,
I may be over my head, but I ll try
Is there somewhere that I can get direction to uninstall with out wiping out therest of my 1st or 2nd HD (second is where I installed Ubuntu
Thanks Again
Norm
:)

---

### Post by gn2 on 2006-11-01
Before you do anything else I would suggest you get a "Super Grub Disk" ready: [http://adrian15.raulete.net/grub/](http://adrian15.raulete.net/grub/)

If you have a Windows install CD, boot it and in recovery console run "fixmbr" this replaces the original Master Boot Record.

---

### Post by Herman on 2006-11-01
It is very simple to uninstall Grub from your MBR, all you need to do is overwrite it's 'IPL' (or 'pointer') in the MBR that makes the MBR point to the Ubuntu partition, with the 'IPL' code that makes the MBR point to the Windows partition again, basically. Gn2 is correct, you can do that with a fixmbr command, in your Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") .

Another way to do it is to use Super Grub Disk, and go 'English Super Grub Disk'-->'Windows'-->'[Fix Boot of Windows]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Fix_Boot_of_Windows")'-->, then select your version of Windows from a menu,--> select a hard disk to install Windows 'IPL' code to between 1 and 4, (In case you have that many hard disks).

Or, you can do it with a Windows 98 boot floppy disk, this way, [Click Here.]("http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr")

Then, you can just delete the Ubuntu partitions whenever you like, with partitioning software. 
You can delete the Ubuntu partition first if you want, but you'll get grub error 22 and youi won't be able to use Grub to boot anything, because you will be deleteing the main working part of Grub along with the Ubuntu partition.```
22 : No such partitionThis error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.        
``` So, you will need to replace Grub with some other bootloader.

Another idea, if you enjoy changing operating systems often, and you would prefer a nice Graphical boot manager, would be to try out GAG Boot Manager. GAG will boot Windows for your quite readily, and is very simple to use. GAG can be installed to MBR, and the main working part of GAG is installed to the first track of the hard disk, which is normally vacant anyway. That makes it 'operating system independant', so you can install and delete operating systems without having top worry about installing or uninstalling boot loaders ever again if you so desire. For more about GAG, look here, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

Regards, Herman :D

---

