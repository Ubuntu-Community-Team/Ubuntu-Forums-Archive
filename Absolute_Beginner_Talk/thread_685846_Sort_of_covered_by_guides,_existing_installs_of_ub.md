---
title: "Sort of covered by guides, existing installs of ubuntu and xp, dual booting?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Huzudra on 2008-02-02
OK, this seems like it would be answered in guides and such but its not directly answered.

i have an ubuntu install on one drive by itself
i tossed in a HDD with an existing XP install AFTER the ubuntu install

what do i need to do to identify which drive is the XP one?  i know more or less how to add the xp to the menu.lst as i've setup dual boot once before....but that was with an ubuntu install and then clean xp install afterwards or vice versa, not an existing ubuntu install and an existing XP install that have never met and shaken hands.

i just dont know/cant find the command which tells me which drive is which?  i mean i know which is SDA1, SDA2, etc but i dont know which is HD 0,0 or HD 0,1...understand?:confused:  i hope what i'm asking is clear enough here.  both OS's are installed and bootable, but i can only boot XP when the linux drive is unplugged because grub doesnt know the XP HDD is there.

---

### Post by wolfen69 on 2008-02-02
a while back, i had the same situation as you. during initial bootup, you should be able to choose which drive to boot from by pressing F12 (quick boot menu) or another F key(sometimes F10). i did it that way for a long time. try it.

---

### Post by jan quark on 2008-02-02
try 

```
sudo fdisk -l
```

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)
this is a good guide for various installation plans

---

### Post by Huzudra on 2008-02-02
sudo fdisk -l lists me the partitions....which i already know.  i want sda2 to be on the grub boot list, but i dont know what drive HD (0,0 0,1 1,1 etc) sda2 sets on.  got it?

---

### Post by Huzudra on 2008-02-02
> **wolfen69 said:**
> a while back, i had the same situation as you. during initial bootup, you should be able to choose which drive to boot from by pressing F12 (quick boot menu) or another F key(sometimes F10). i did it that way for a long time. try it.

i'll try to find what key does that, this foxconn board has poor documentation.

---

### Post by Huzudra on 2008-02-02
ok now this is weird, i got the XP install re-validated and have been toying with it...with the ubuntu drive UNPLUGGED. now i have to unplug the XP drive to boot Ubuntu?  what the hell did i do here?  i installed nothing.  prior to this i had been booting right to ubuntu with grub with the XP drive plugged in but the install not functioning due to me never booting to it to validate the XP install.

---

### Post by Huzudra on 2008-02-02
so i'm trying that guide and working under the assumption i would do it like if i had installed ubuntu and then xp....

i'll update if this works or how badly i've broken things :lol:

ok, i'm learning to fish so to speak (again that is, i used to know this stuff)

i got my grub fixed, i can boot ubuntu with both drives plugged in again.

however im still a little cofused at one bit.

my pc differs from the guide because i'm using 2 seperate drives. so HD 0,0 and HD 1,0 are my 2 drives right?  HD 0,0 is which and HD 1,0 is which?  i think i buggered up the menu.lst a little bit, selecting XP does nothing...probably because i have it associated with the wrong drive.  so thus begins again...how do i tell which drive is being labelled as which?

---

### Post by Huzudra on 2008-02-02
ok so i found why my xp selection wasnt doing anything, my chainloader and makeactive bits somehow got smushed into one line.

so i fixed that and now i just get error 17 in grub and cant boot to anything and i know exactly why this is.

its because grub is being told theres a HDD present that is not there because i dont ******* know which HDD is which!  trial and error evidently was not the right way to figure out which drive has the XP install.  so now i need help with 2 things

1. fix error 17
2. identify correctly which drive is which. 


i know the ubuntu sata drive is HD 0,0 and now i know that the XP drive is NOT HD 1,0

i thought i had just fixed error 17 by booting to the livecd, removing my changes to the menu.lst and rebooting. no, error17 remains!  what the heck?

---

### Post by Shazaam on 2008-02-02
The drive that boots first is always hd0.0. and it depends on how you have the boot order set up in your bios. So if you change the bios boot order you have to edit grub accordingly.
This page helps explain grub configuration and errors........

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Huzudra on 2008-02-02
> **Shazaam said:**
> The drive that boots first is always hd0.0. and it depends on how you have the boot order set up in your bios. So if you change the bios boot order you have to edit grub accordingly.
This page helps explain grub configuration and errors........

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

i changed nothing in BIOS.  the only change i did was to correct my menu.lst from having 

makeactivechainloader+1 

to

makeactive
chainloader +1

i'll post my current menu.lst from the linux machine in just a minute.

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
# kopt=root=UUID=dbbba494-44c4-4659-9bec-1526559ba068 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dbbba494-44c4-4659-9bec-1526559ba068 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dbbba494-44c4-4659-9bec-1526559ba068 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  de  Dell Utility
/dev/sda2               7        9366    75184200    7  HPFS/NTFS
/dev/sda3            9367        9725     2883667+  db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000937ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29645   238123431    6  FAT16
/dev/sdb2           29646       30401     6072570    5  Extended
/dev/sdb5           29646       30401     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> find /boot/grub/stage1

Error 15: File not found

grub> 

```

---

### Post by Huzudra on 2008-02-02
help, what do i do to fix it?

---

### Post by Shazaam on 2008-02-02
According to the menu.lst that you posted there isn't any entry for Windows. And your fdisk doesn't show your Ubuntu partition.
Windows is supposed to be on sda and Ubuntu is supposed to be on sdb correct? Is that fat16 partition on sdb supposed to be Ubuntu?
This is my fdisk.....

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38626   310263313+   5  Extended
/dev/sda5               1         781     6273319+  82  Linux swap / Solaris
/dev/sda6             782        3350    20635461   83  Linux
/dev/sda7            3351        8471    41134401   83  Linux
/dev/sda8            8472       26554   145251666   83  Linux
/dev/sda9   *       26555       38626    96968308+  83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

```

---

### Post by Huzudra on 2008-02-02
yea, i dont know what the hell happened to my **** man.

i put my menu.lst back to how it was because i dont know which drive is which for the menu.lst....and i still get error 17!

as for the fdisk that fat16 partiton shouldnt be there...i did the default ubuntu install on the 250gb drive which would have been ext2.  what the heck is going on?  all of my data is intact when i boot from the livecd.  is there someway to nuke grub and totally reinstall it?

---

### Post by Huzudra on 2008-02-03
after a little bit of investigating here....

hdd with XP does not have grub on it, boot record is set to wrong partition though

hdd with ubuntu has broken grub

i'm going to....fix the boot record on the XP hdd so i have atleast a bootable system then get down into fixing grub.

whats the best way to fix it?  can i remove and then reinstall it?  why did i have a dream about a lion on a beach chasing me?  stay tuned to the next post for all this and more! :lolflag:

---

### Post by Big_Rog on 2008-03-04
No luck in sorting this out?  I'm about to attempt a similar setup due to lack of proper Ventrilo support and the monkeyshines involved in installing most non-native apps.  I've got an empty drive that i'd like to put windoze on, but the tutorial on apcmag only covers a single drive install, not a dual drive.  I'd hate to kill my existing install, and drive space is at a bit of a premium, so i'm not too sure about having room to back up all my Linux files.  I'm still trolling the forums to see if someone else got this to work, but your input would be great!

---

### Post by Huzudra on 2008-03-21
well i ended up nuking the XP install and doing a clean one.  playing with 8.04 Wubi on the XP install at the moment.  i'll do a full blown install later in april with 8.04 stable.  its pretty nice btw!

now that i have an XP install and am doing an Ubuntu install later i dont think i'll have problems again....only issue may be correctly identifying which drive is which during the grub configuration.

how exactly do i know which drive grub is calling hdd0 and which is hdd1?  i know how to tell which partition is what, but dont know how grub decides to name drives.  same PC as i've discussed earlier in the thread.

---

### Post by Big_Rog on 2008-03-22
if i recall correctly, grub starts at 0, whereas sda/hda starts at 1:.e.g. drive 1, partition 1 in grub is (hd0,0).  drive 2, partition 1 is (hd1,0) etc.  I have another post around here somewhere with a link to apcmag.com that has complete instructions for installing lots of different configurations, though no direct instructions for 2 physical drives.

---

### Post by Huzudra on 2008-03-22
> **Big_Rog said:**
> if i recall correctly, grub starts at 0, whereas sda/hda starts at 1:.e.g. drive 1, partition 1 in grub is (hd0,0).  drive 2, partition 1 is (hd1,0) etc.  I have another post around here somewhere with a link to apcmag.com that has complete instructions for installing lots of different configurations, though no direct instructions for 2 physical drives.

that helps alot actually.  thankyou!  i didnt understand the naming scheme, but that explanation makes sense now.  so the drive numbered 0 would be the drive at #1 in the boot order of the bios then?  i know when i install i need to have grub on the drive that linux is so that if the windows drive gets pulled from the PC to be swapped for a new or faster drive i can do so without an error 15.

---

### Post by Big_Rog on 2008-03-23
I'm not sure about boot order from the bios, I think it just has to do with the location/channel of the dirve, i.e. SATA 1, 2, or IDE 1 master/slave.  Before I installed grub on my windows drive, I used the bios to change the boot order.  Crude and time consuming, but effective.  Grub only takes a few minutes to install, and once you understand the config options it's no worse than tweaking your old config.sys and system.ini files. =P

The primary reason for putting the windows drive first physically is the whole "windows wants to be installed on C:\" issue.  As a workaround for that, I suppose you could go into safe mode->administrator and use the drive configuration tool to force the windows drive letter to C:\.

---

