---
title: "Problem in triple booting."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-12-25
I have installed XP, vista and ubuntu on my system with ubuntu being the latest one to install but I am not able to boot into XP or vista in the grub. There are 4 items in the grub with 3 ubuntu items one one vista/Longhorn item. When I click the vista/longhorn irem, the system simply restarts. Please help me. My menu.1st is as follows,


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
# kopt=root=UUID=4e83899b-1031-417d-b32e-d56815ee4d10 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e83899b-1031-417d-b32e-d56815ee4d10 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e83899b-1031-417d-b32e-d56815ee4d10 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista / Longhorn (Loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by meierfra on 2007-12-25
Open a terminal (Applications->Accessories->Terminal) , type

```
sudo fdisk -l
```

and post the output.

---

### Post by Rabindranath on 2007-12-25
The output is,


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc3afc3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2416    19406488+   7  HPFS/NTFS
/dev/sda2            2417        9728    58733640    f  W95 Ext'd (LBA)
/dev/sda5            2417        4832    19406488+   b  W95 FAT32
/dev/sda6            4833        7248    19406488+   7  HPFS/NTFS
/dev/sda7            9665        9728      514048+  82  Linux swap / Solaris
/dev/sda8            7249        9664    19406488+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43c2a0f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2        6503    52227283+   7  HPFS/NTFS
/dev/sdb6            6504       13005    52227283+   7  HPFS/NTFS
/dev/sdb7           13006       19507    52227283+   7  HPFS/NTFS
/dev/sdb8           19508       30401    87506023+   7  HPFS/NTFS

---

### Post by Biggy on 2007-12-25
install Startup-Manager

---

### Post by Rabindranath on 2007-12-25
How to instal startup- manager? It isn't available in the add or remove programs. I think it is available for windows only. I am not able to boot into either XP or Vista now. :(

---

### Post by meierfra on 2007-12-25
I don't see any reason why you aren't able to boot into Vista. So I will have to ask a bunch of question to figure out what is going on.

Is Vista  on sda1, that is the first partition on  the 80 G drive?

Is XP   also on the 80 G drive?

Did you install Vista after XP?

Had you been able to boot into XP and Vista before you installed Ubuntu?

Did you change the boot order during or after the installation process?

Are your bios set to boot from the 80G drive?

Did you delete any partitions when you installed Ubuntu?

Did your resize any partitions  when you installed  Ubuntu?

What program did you use to do the partioning? (gparted, Ubuntu Installer, Vista Disk management, Partition Magic,...)

---

### Post by Rabindranath on 2007-12-25
XP is on sda1. XP, Vista and ubuntu are on the 80G drive. I installed XP first, then vista then ubuntu. I was able to boot into both vista and XP before I installed ubuntu. I didn't delete or resize any partition during ubuntu setup. I used the XP disk to partition the 80G drive. The first drive to boot in th bios configuration is the 80G drive. Thanks for your reply.

---

### Post by Bartender on 2007-12-25
/dev/sda1 * 1 2416 19406488+ 7 HPFS/NTFS
/dev/sda2 2417 9728 58733640 f W95 Ext'd (LBA)
/dev/sda5 2417 4832 19406488+ b W95 FAT32

I'm not great at reading this stuff, so probly wrong.  Doesn't the above indicate that XP is inside an extended (logical) partition?
I thought Windows couldn't boot from an logical partition.  Has to be primary.  
Can you post a picture of your partitions from GParted?

Nope, never mind, if you were able to boot into XP before installing Ubuntu...

---

### Post by terminal on 2007-12-25
In my system this happens when i have  windows installed on first hard disk and linux on second hard disk and from bios selection menu i force it to boot from second hard disk ( which has grub ) . Now when i select to boot Windows through grub which sees windows hd as hd1 while physically it is hd0 . Due to this Xp just reboots .  Can you tell which partition has XP and which one has Vista  installed ? 

Try removing "makeactive" from grub.conf .


Edit read your reply after posting this .

---

### Post by Rabindranath on 2007-12-25
All the 3 OSes are in the same 80G hard disk. XP is in sda1, sda6 has vista. But grub seems to see only vista. When I installed ubuntu I was able to see vista/longhorn in the grub and not XP.

---

### Post by terminal on 2007-12-25
As i know Vista just edits xp's bootloader and boot itself from there . I am not sure if this will work but can you check if vista will boot by doing this ( not sure bcoz i dunno if vista sets boot laoder on its own partition or not ) . 

root (hd0,5)
chainloader +1 


One more question : When u select Vista/XP from grub , do u get Vista /Xp selection screen or it reboots without showing anything ?

---

### Post by Rabindranath on 2007-12-25
When I changed (hd0,0) to (hd0,5) it shows an error saying,

"Error 12: Invalid device requested"

      When it is default ie, (hd0,0), and when I click " Windows Vista/Longhorn (loader)" it simply restarts without showing the vista/xp selection scren.

---

### Post by meierfra on 2007-12-25
> I used the XP disk to partition the 80G drive. 

This might be the problem. Let's hope you did not damage the Vista partition.

Are you able the access Vista and XP from Ubuntu? Post the output of

```

mkdir XP
sudo mount -t ntfs /dev/sda1 XP
mkdir Vista
sudo mount -t ntfs /dev/sda6 Vista

```

---

### Post by Rabindranath on 2007-12-25
When I do 

mkdir XP
sudo mount -t ntfs /dev/sda1 XP
mkdir Vista
sudo mount -t ntfs /dev/sda6 Vista


There are 2 folders created in my home folder with names XP and Vista. The Contents of the folders are the respective files and foldres in XP and Vista partitions where I installed them. Is there any output I should post?

---

### Post by meierfra on 2007-12-25
That's good news. Seems your partitions are intact. But it also means I have no idea what the problem could be. Your original item in menu.lst really should have worked.  
Get SuperGrub (see my signature). Maybe it succeeds to boot Xp and Vista.

Do you have a Vista CD? If yes, you can use it to fix the MBR and the VIsta boot sector.

---

### Post by Rabindranath on 2007-12-25
I have vista dvd and I was able to fix the mbr by bootrec/fixmbr but ubuntu is gone. I have only XP and Vista now :( . Do I have to know the terminal to use the supergrub disk?

---

### Post by meierfra on 2007-12-25
Are Vista and XP working?


Fixing Grub is easy:

Boot from the Ubuntu LiveCD, open a terminal

and type

```
sudo grub
```

and at the "grub>" prompt

```

root (hd0,7)
setup (hd0)
quit

```

This will get  ubuntu back, And if you are lucky also Vista and XP.

---

### Post by meierfra on 2007-12-25
> Do I have to know the terminal to use the supergrub disk?

No. But since you already got  Vista and XP to boot, I don't think SuperGrub would do any good. But I suggest downloading it anyway.  I'm sure it will come in handy sometime.

---

### Post by meierfra on 2007-12-25
If you did not get Vista to boot after you  reinstalled Grub, here is one more think to try:

use

title Windows Vista / Longhorn (Loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

in menu.lst (so just replace "root" by "rootnoverify"

(Sorry, I should have suggested that a long time ago)

---

### Post by Rabindranath on 2007-12-25
I am able to boot XP and Vista when I try to fix the mbr. When I try to restore grub, I get the same problem of rebooting when clicking on "Vista/Longhorn (loader)". But when I change "root" to "rootnoverify". It shows a message "Starting up..." in the grub and doesnot proceed further.

---

### Post by meierfra on 2007-12-25
Sorry, I have no idea what is going on.  Since we can't get Grub to work, I suggest to use [EasyBCD]("http://neosmart.net/dl.php?id=1")

I don't know much about EasyBCD. But I know that it is pretty easy to use and that you need to install Grub to the boot  sector of the Ubuntu Partition. The latter gone be done via:


```
sudo grub
root (hd0,7)
setup (hd0,7)
```

You also need to restore the MBR again, but you already know how to do  that.

---

### Post by Rabindranath on 2007-12-25
Thank you very much meierfra:KS. Ill try EasyBCD.

---

### Post by Rabindranath on 2007-12-27
I installed EasyBCD today and it worked like a charm. I followed this.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Thanks meierfra for the info.

---

