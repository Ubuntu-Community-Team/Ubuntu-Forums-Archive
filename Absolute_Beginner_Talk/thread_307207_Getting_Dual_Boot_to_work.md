---
title: "Getting Dual Boot to work"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by EricK33 on 2006-11-26
Before trying to install Ubuntu 6.10 my set up was as follows:

C:\ drive with WinXP(Home) on
D:\ drive (a separate 100G hard drive) with about 50G of stuff on it.

I made a LiveCD and that worked fine so I ran the installer. The installer asked where I wanted to put it so I chose the D:\ drive. It then partitioned the drive (about 70/30) and installed Ubuntu (at least I assume it did) on the 30G partition. When it had finished it asked me to restart so I did (removing the LiveCD first!) and it booted straight into Windows.

Windows came up with a message saying something like there were incosistencies with the D:\ Drive and then it ran Checkdisk.

Basically, Windows is working fine, and the D: drive reports as 70G in size and all my stuff seems to be on there, but how do I get Ubuntu to start?

Thanks for any help.

Eric

---

### Post by MozUK on 2006-11-26
i have the same problem except I have windows XP and ubuntu installed on different partitions of the same drive, can anyone help us? thanks

---

### Post by bulldog on 2006-11-26
> **MozUK said:**
> i have the same problem except I have windows XP and ubuntu installed on different partitions of the same drive, can anyone help us? thanks

You can reinstall GRUB from the live cd in 5 minutes.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.


@EricK33,
You can do the same but if you can,I should try to boot from the second hard disk,to see if GRUB is in the MBR of that drive.

If GRUB is on the second hdd,make this the master boot device and add your windows,if not done already,to the menu.lst and map your hdd's.
Check this and if GRUB is on the other hdd we'll take it from there.

---

### Post by EricK33 on 2006-11-26
Thanks Buildog,

I set my other HDD as the top bootable drive and I got a menu with both Ubuntu and Windows. So that looks OK.

I am writing this from within Ubuntu!

I haven't yet tried to boot Windows from the menu though :)

---

### Post by bulldog on 2006-11-26
> **EricK33 said:**
> Thanks Buildog,

I set my other HDD as the top bootable drive and I got a menu with both Ubuntu and Windows. So that looks OK.

I am writing this from within Ubuntu!

I haven't yet tried to boot Windows from the menu though :)
Well I'm pretty sure windows won't boot :D 

You have to alter your windows entry in menu.lst like this,```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

If you have done,I'll think your windows will boot fine.
Just give it a try and let me know.

---

### Post by EricK33 on 2006-11-26
Where is menu.lst and how do I update it?

Imagine I have never used Linux before in my life:)

---

### Post by nickpaton on 2006-11-26
Open Terminal ( Applications > Accessories)

And at the prompt type (or copy and paste from here):

```
gksudo gedit /boot/grub/menu.lst
```

It will open a new window (ignore any error messages)

Scroll to the lines which Bulldog says, amend them and save and close that window.

Then do a reboot and see if you can get into Windows and Ubuntu.

Good luck!

BTW Welcome to the forums!!

---

### Post by EricK33 on 2006-11-26
Thanks.

I am writing this one from within Windows!

When I rebooted the menu had three Ubuntu options (which I think I understand) and two Windows options. The first one didn't work as it said there was a dll missing, but the second one did. It's not really a problem as I can always use the second one, but is there any reason for this?

---

### Post by bulldog on 2006-11-26
Not a real reason just comment ## all the lines from this entry.
If you don't need it you can delete the lines completely if you want.

---

### Post by MozUK on 2006-11-26
I cant work out how Im meant to do this line:

[PHP]grub> find /boot/grub/stage1
find /boot/grub/stage1
[/PHP]

when i enter grub> find /boot/grub/stage1 the line is just sent straight back to me, shouldn't i be getting a hard drive location here ? help! :???: 

thanks

---

### Post by bulldog on 2006-11-26
Yes you should get a location like (hd0,1) or something like that.
Can you put the outcome of```
sudo fdisk -l  (l as in like)
```on the forum,so we can see how you partitioned your hdd?

---

### Post by MozUK on 2006-11-26
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          65      522081   82  Linux swap / Solaris
/dev/sda2              66        6439    51199155   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650        7714      522112+  82  Linux swap / Solaris
/dev/sdc3            7715       14946    58091040   83  Linux

```

---

### Post by MozUK on 2006-11-26
can anyone help ? I really want to use ubuntu it looks great, just cant work this bit out though :(

oh and btw i resize in the graphical ubuntu installation process and i cant see my new linux partition's in XP not sure if im meant to

---

### Post by bulldog on 2006-11-26
> **MozUK said:**
> ```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          65      522081   82  Linux swap / Solaris
/dev/sda2              66        6439    51199155   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650        7714      522112+  82  Linux swap / Solaris
/dev/sdc3            7715       14946    58091040   83  Linux

```

Oke,you have three Sata drives and two with a linux partition.
Which one do you want to boot?
You have a linux on sda and one on sdc.
Don't know if this was the intention to install both.

If you can give us your menu.lst we can see how things are configured.
```
cat /boot/grub/menu.lst
```
As I can see you have a 320GB sda with a Linux install,a sdb 80GB with a windows install and sdc 123GB with a windows partition and a Linux swap and linux partition.

---

### Post by MozUK on 2006-11-26
yes sorry im having trouble with my 300gb drive atm, im trying to install linux on the other one, this one:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650        7714      522112+  82  Linux swap / Solaris
/dev/sdc3            7715       14946    58091040   83  Linux
```

---

### Post by bulldog on 2006-11-26
When you boot the live cd and you want to see your installed menu.lst type in your terminal```
sudo mkdir /mnt/rescue
```to make a mount point.
To see what partition you have to mount```
sudo fdisk -l (l as in like)
```
Mount the partition```
sudo mount /dev/sdb3 /mnt/rescue
```I presume it's sdb3 but take a look if I'm right about that it should be as it is the first boot device.

If the mounting is done to find your menu.lst```
cat /mnt/rescue/boot/grub/menu.lst
```
Post this on the forum so we can have a look at it.

If GRUB is not installed properly you can do that now by the code in a previous post.

---

### Post by MozUK on 2006-11-26
heres my menu.lst

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=946daeb2-d814-4300-855c-f54c4446950c ro
# kopt_2_6=root=/dev/sdc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,2)

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdc3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdc3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1


```

---

### Post by bulldog on 2006-11-26
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=946daeb2-d814-4300-855c-f54c4446950c ro
# kopt_2_6=root=/dev/sdc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
rootnoverify            (hd1,0)
savedefault
makeactive
##map             (hd0) (hd1)
##map             (hd1) (hd0)
chainloader     +1
```

This is what it should be.
You can copy paste it into your menu.lst [just remove all what in it and put this instead.
Just save it as menu.lst this is important!!!

---

### Post by Mgcross on 2006-11-26
I could use some help as well...here is the output from sudo fdisk -l



Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         951     7638876   83  Linux
/dev/hda2             952        2482    12297757+   b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       19457   156039345    5  Extended
/dev/hdb5              32       19457   156039313+  8e  Linux LVM

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4869    39110211    7  HPFS/NTFS

Any help adding winxp to grub would be most appreciated!!

---

### Post by Ru$$i@N on 2006-11-26
I have problems getting any of my 2 OS's to boot when both HDD's are connected. ](*,) 
Alright, so I have 2 SATA HDD's. On one of them i've got WinXPHome, on the other i've got Ubuntu.

Right now I have only Ubuntu hdd connected.
Here's what fdisk gives me:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30262   243079483+  83  Linux
/dev/sda2           30263       30401     1116517+   5  Extended
/dev/sda5           30263       30401     1116486   82  Linux swap / Solaris

```
Sorry, can't show you what's going on on the other drive.

And here's a portion of menu.lst I have so far:
```

title		Microsoft Windows XP Home
map 		(hd0) (hd1)
map 		(hd1) (hd0)
rootnoverify 	(hd0,0)
savedefault
chainloader	+1

title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

```

When both of HDD's are connected with the above settings I get when I try to boot WinXP:
```

Error 13: Invalid or unsupported executable format

```

and when I try to boot Ubuntu I get:
```

Error 17: Cannot mount selected partition

```

:confused: 

I'm in Ubuntu right now, with XP HDD disconnected. Each time I have to change "root (hd1,0)" to "root(hd0,0)" to boot Ubuntu. :-? 

PLEASE HELP!

---

### Post by confused57 on 2006-11-26
> **Ru$$i@N said:**
> I have problems getting any of my 2 OS's to boot when both HDD's are connected. ](*,) 
Alright, so I have 2 SATA HDD's. On one of them i've got WinXPHome, on the other i've got Ubuntu.

Right now I have only Ubuntu hdd connected.
Here's what fdisk gives me:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30262   243079483+  83  Linux
/dev/sda2           30263       30401     1116517+   5  Extended
/dev/sda5           30263       30401     1116486   82  Linux swap / Solaris

```
Sorry, can't show you what's going on on the other drive.

And here's a portion of menu.lst I have so far:
```

title		Microsoft Windows XP Home
map 		(hd0) (hd1)
map 		(hd1) (hd0)
rootnoverify 	(hd0,0)
savedefault
chainloader	+1

title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

```

When both of HDD's are connected with the above settings I get when I try to boot WinXP:
```

Error 13: Invalid or unsupported executable format

```

and when I try to boot Ubuntu I get:
```

Error 17: Cannot mount selected partition

```

:confused: 

I'm in Ubuntu right now, with XP HDD disconnected. Each time I have to change "root (hd1,0)" to "root(hd0,0)" to boot Ubuntu. :-? 

PLEASE HELP!
First of all set it in your bios to boot first to the SATA drive containing Ubuntu.
Change your Windows entry to rootnoverify (hd1,0) and your Ubuntu entries to root (hd0,0).
You shouldn't need to change or edit anything else to boot Windows or Ubuntu.

This is how I have my system set up, but should work fine with 2 SATA drives, as long as you boot first to the Ubuntu drive:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by bulldog on 2006-11-27
> **Mgcross said:**
> I could use some help as well...here is the output from sudo fdisk -l



Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         951     7638876   83  Linux
/dev/hda2             952        2482    12297757+   b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       19457   156039345    5  Extended
/dev/hdb5              32       19457   156039313+  8e  Linux LVM

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4869    39110211    7  HPFS/NTFS

Any help adding winxp to grub would be most appreciated!!

Presuming windows is one hdd1 your windows entry in menu.lst should be```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd2,0)
savedefault
chainloader	+1
```

hda is (hd0), hdb is (hd1) and hdd is (hd2)
I'm also presuming you boot from hda and GRUB is located on that disk.
Just give it a try and let us know if it worked.

---

### Post by MozUK on 2006-11-27
im getting error 22 no partition exists now! this is a nightmare! :( can anyone help?

---

### Post by Mgcross on 2006-12-04
thanks, going to try this now!
I'll let you know!

---

