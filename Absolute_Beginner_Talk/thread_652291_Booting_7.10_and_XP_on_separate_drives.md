---
title: "Booting 7.10 and XP on separate drives"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Tombo5150 on 2007-12-28
Hello, after all the problems my parents had been expressing I finally convinced them to let me put in a separate drive for linux. I successfully installed Gutsy 7.10 on the drive. Now lies the problem, how do I setup a menu to where they can choose whether to select the Windows drive, or the linux drive? I have the linux drive setup as the slave currently and the  windows as the master. I was reading in a few threads like this one: [http://ubuntuforums.org/showthread.php?t=650848](http://ubuntuforums.org/showthread.php?t=650848) and it seems you can do something like this with GRUB. I want to make it so that grub would come up and you had 10 seconds or so to boot into ubuntu if you wanted to, otherwise it would go straight to windows. Is any of this possible?


*EDIT*
A friend showed me this site which shows how to do this thing. However, it has linux setup as the master drive and windows as the slave. This is not what I need though, I need Windows to be the primary boot. [http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)

---

### Post by markharding557 on 2007-12-28
as far as i know grub should work irrespective of what drive you put ubuntu on
grub is automaticaly installed by ubuntus installer
it may be grub has not installed correctly

---

### Post by dstew on 2007-12-28
If you already installed the Ubuntu system on your hard drive, you will need to install the grub boot loader to be able to select either system. Windows boot loader cannot boot any other operating system but Windows.

To install grub, boot an Ubuntu LiveCD, open a terminal and enter these command:```
grub

```This will start the grub command line, which has the grub> prompt. Enter at the grub> prompt```
find /boot/grub/stage1
```It will return the grub-name for the grub root directory, like (hd0,1). Use whatever root it gives you in these commands:```
root (hd0,1)
setup (hd0)
quit
```Then reboot, and let us know what happens.

---

### Post by Tombo5150 on 2007-12-28
Grub works fine when I boot the linux drive. However, if I don't have the BIOS setup so the linux drive boots, then it boots the windows drive and I don't have a choice of which drive to boot. How do I get that choice? Am I clear that I want it to boot directly to windows, but I just want like 10 or 15 seconds where I am given the choice to boot into Ubuntu or not.

---

### Post by Tombo5150 on 2007-12-28
> **dstew said:**
> If you already installed the Ubuntu system on your hard drive, you will need to install the grub boot loader to be able to select either system. Windows boot loader cannot boot any other operating system but Windows.

To install grub, boot an Ubuntu LiveCD, open a terminal and enter these command:```
grub

```This will start the grub command line, which has the grub> prompt. Enter at the grub> prompt```
find /boot/grub/stage1
```It will return the grub-name for the grub root directory, like (hd0,1). Use whatever root it gives you in these commands:```
root (hd0,1)
setup (hd0)
quit
```Then reboot, and let us know what happens.

When I typed the 'find' command I got an Error 15: File not found.

:-!

---

### Post by Moop on 2007-12-28
You will need to boot the linux drive to get the choice of XP or Ubuntu. You can change the default OS (which one boots as default) once you get grub installed. 

If you didn't install grub then maybe just reinstall Ubuntu and let it install grub normally.

---

### Post by Tombo5150 on 2007-12-28
Reinstall Ubuntu? I just installed it last night, why would grub not install correctly? Is there a way to just reinstall grub and not the whole OS?

---

### Post by Moop on 2007-12-28
I thought maybe you had chose not to install grub since you had the error message about file not found. 

Yes you can just re-install grub.

---

### Post by meierfra on 2007-12-28
You do not have to reinstall anything. You just need to edit  the file "menu.lst"


Boot to ubuntu. Open a terminal  (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```
(both "l" are lowercase L)

With that information I can tell you how to edit "menu.lst"

---

### Post by Tombo5150 on 2007-12-28
alright heres what I got:

```
user@-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01380137

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099225

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4701    37760751   83  Linux
/dev/hdb2            4702        4865     1317330    5  Extended
/dev/hdb5            4702        4865     1317298+  82  Linux swap / Solaris

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bfb69

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       48641   390708801    b  W95 FAT32

```

and 

```
user@-desktop:~$ cat /boot/grub/menu.lst 
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
# kopt=root=UUID=0a5cc479-14d7-4974-b48f-3e5556313536 ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0a5cc479-14d7-4974-b48f-3e5556313536 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0a5cc479-14d7-4974-b48f-3e5556313536 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Thank you so much.

---

### Post by meierfra on 2007-12-28
Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```


This open the file menu,lst


Change   

hiddenmenu

to 

#hiddenmenu

Change

timeout 3

to 

timeout 10

(this will give you 10 seconds to choose ubuntu)



Look  for the line


#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST


Just BEFORE  that line  insert


title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

Save the file and  reboot.

Since you have three harddrives, there is a slight chance that this does not work. Then  just come back here for more help.

---

### Post by Tombo5150 on 2007-12-30
I'll try it. I don't have three harddrives only two. Right now I have a jumper on my linux drive and it's setup to be the slave. I understand I need to make it the master drive. Will taking the jumper off and putting the jumper on the windows drive in it's respective slave position work for me? Or will I need to get another jumper so I can put them both on a drive? If so, where can I purchase a jumper?

---

### Post by meierfra on 2007-12-30
> I don't have three harddrives only two.

Your fdisk shows three hard drives.

hda: 40 GB drive with NFTD partition.
hdb: 40 GB drive with Ubuntu
sde:  400 GB drive with Fat 32 partition.

Maybe you have a some kind of raid, which you do not  know about?

> Right now I have a jumper on my linux drive and it's setup to be the slave. I understand I need to make it the master drive. 

Try  my suggestion first, and  then we worry about that.

---

### Post by Tombo5150 on 2007-12-30
Your suggestion worked! However, my parents computer is retarded and the arrow keys won't move so now I can't select Ubuntu to start it! Wonderful right? Any ideas as to why this is happening?

---

### Post by Tombo5150 on 2008-01-02
Okay, I've got that last problem solved. Now that I've figured out the GRUB situations, how about making this drive the master drive?

---

