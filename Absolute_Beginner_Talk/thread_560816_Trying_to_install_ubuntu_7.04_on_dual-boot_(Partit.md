---
title: "Trying to install ubuntu 7.04 on dual-boot (Partition problem)"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by b21bballer on 2007-09-26
I have XP on my laptop and I'm trying to load Ubuntu 7.04.

My partitions are as follows:

/dev/sda1
fat16
41 mb

/dev/sda2
nts
56606 mb

/dev/sda3
ext3
18070 mb

/dev/sda4
swap
3800 mb

When I select the partition /dev/sda3 I get: "Warning! File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 20017 (39957 expected; size of FATs is 79 sectors (157 expected)." followed by "The test of the file system with type fat 16 in partition #1 of SCSI1 (0,0,0) found uncorrected errors. If you do not go back to the partitioning menu and correct these errors, the partition will be used as is."

WHAT DO I DO!? :mad::mad::mad:

---

### Post by the.phantom on 2007-09-26
i am not a expert!

what is the fat 16 for?

you can have Ubuntu read/write in ntfs 

i just cheated and created a fat32 partition and works for me 
and both can rewd/write in it

---

### Post by b21bballer on 2007-09-26
I'm not sure what that is. It was there.

I guess I'm looking for a guide to show me how to install so that I can dual-boot.

:(

---

### Post by the.phantom on 2007-09-26
ok go here
[http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1_Ogg_Medium](http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1_Ogg_Medium)

click the "download" in the bottom left or you can click the upper left and pic a different format say flash 

hope this helps?

---

### Post by rickycodie on 2007-09-26
dual booting is very easy. first i would wipe the fat 16 partition and then install over the ext3. ubuntu will automatically set up your boot selector(grub) and allow you to choose windows or ubuntu.

---

### Post by b21bballer on 2007-09-26
> **rickycodie said:**
> dual booting is very easy. first i would wipe the fat 16 partition and then install over the ext3. ubuntu will automatically set up your boot selector(grub) and allow you to choose windows or ubuntu.

Ok, I'm just being cautious so I do not lose the XP.

---

### Post by Ptero-4 on 2007-09-27
b21bballer. You don't need to worry about your windoze. Ubuntu IIRC doesn't do automatic virus removal yet.

---

### Post by eph1973 on 2007-09-27
FAT16 is pretty old now.  It's from back when MS-DOS was used, and a little bit into Windows 95, if I remember correctly.  Windows XP uses the NTFS partition.  Make sure you don't mess with that one, and you should be fine.

---

### Post by handydan918 on 2007-09-27
> **b21bballer said:**
> I have XP on my laptop and I'm trying to load Ubuntu 7.04.

My partitions are as follows:

/dev/sda1
fat16
41 mb

/dev/sda2
nts
56606 mb

/dev/sda3
ext3
18070 mb

/dev/sda4
swap
3800 mb

When I select the partition /dev/sda3 I get: "Warning! File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 20017 (39957 expected; size of FATs is 79 sectors (157 expected)." followed by "The test of the file system with type fat 16 in partition #1 of SCSI1 (0,0,0) found uncorrected errors. If you do not go back to the partitioning menu and correct these errors, the partition will be used as is."

WHAT DO I DO!? :mad::mad::mad:

If I don't miss my guess, the FAT16 partition is a restore partition. I would leave that AND the ntfs partition alone.
Backing up critical data is always recommended. But after dozens of linux installs, I have never borked a windows partition. So relax, and let the installer do it's job.:)
BTW, The swap partition looks a little excessive. 1.5-2.0 times the amount of RAM you have is a reasonable rule of thumb.

---

### Post by b21bballer on 2007-09-27
> **handydan918 said:**
> If I don't miss my guess, the FAT16 partition is a restore partition. I would leave that AND the ntfs partition alone.
Backing up critical data is always recommended. But after dozens of linux installs, I have never borked a windows partition. So relax, and let the installer do it's job.:)
BTW, The swap partition looks a little excessive. 1.5-2.0 times the amount of RAM you have is a reasonable rule of thumb.

Well the installer is giving me that error message when I tried to let it do it..

---

### Post by zhanglini on 2007-09-27
I have a dual boot on my computer too (Feisty/XP).  But somehow I can use my FAT32 from XP, but I can't find it under Feisty.  
Anybody knows what I am supposed to do so I can use it under Linux?
Thanks in advance

---

### Post by b21bballer on 2007-09-27
So does everyone think it is ok to overwrite the FAT16?

That's the only way I can see that this may actually work..

---

### Post by Niniel on 2007-09-27
No, don't!

Unless you want to lose your restore partition.
If you have a WinXP installation CD and a CD with the apps/drivers that came with your box, you may need that stuff.
I suppose you could clone it to an external hd, but it's so small, why take chances?
Unless of course you totally want to get rid of Windoze, then it won't matter.

---

### Post by Ozeuss on 2007-09-27
I'm not sure what the FAT16 is for, but i would leave it alone. Its size is too small and you won't be able to use it for anything else. When you boot into the ubuntu live cd, use gparted to wipe the ext3 and swap, leaving an unused space (unless you have data in the ext3 partition). 
Then, install using "Use largest continuous space" option.

---

### Post by handydan918 on 2007-09-27
> **b21bballer said:**
> Well the installer is giving me that error message when I tried to let it do it..
This error?
> If you do not go back to the partitioning menu and correct these errors, the partition will be used as is."

Sounds like the installer was expecting to see something in particular, and a FAT16 file system wasn't it. I would disregard and continue with the install.

---

### Post by b21bballer on 2007-09-27
Ok, the system is installed. :guitar:

Another question: how can I change so that XP is the first option on the boot record?

---

### Post by handydan918 on 2007-09-28
> **b21bballer said:**
> Ok, the system is installed. :guitar:

Another question: how can I change so that XP is the first option on the boot record?

```
sudo gedit /boot/grub/menu.lst
```

Once you are looking at that file, there are two ways to change the default boot order. One is to cut and paste the desired section and place it first on the list. 
The other (preferable ?) way is to add the bolded text below;

```
timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1
default <NUM>
```


Where <NUM> is the number of the entry in the menu. Grub generally starts counting at 0, not 1.

if you post your menu.lst, I am sure we can give you more information.

---

### Post by b21bballer on 2007-09-28
Here it is:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

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
# kopt=root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

I really have no idea how to use this OS :confused:

---

### Post by eph1973 on 2007-09-29
Try this out:


Step 1:
Make a backup of your menu.lst (just in case).  In your terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```Step 2:
Edit your current menu.lst to move XP to the top of the list.  You could just change the default number there, but if you get any kernel upgrades, that will change all that, and you'll have to remember so go back and change the number.  This way, your XP should always be defaulted. (You would have to manually select Ubuntu if you wanted to boot to Ubuntu).
In your terminal:
```
sudo gedit /boot/grub/menu.lst
```Step 3:
Since you pasted your menu.lst, I'll repaste it with the changes, then explain them:
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
timeout        20

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
# kopt=root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# on /dev/sda2
title        Microsoft Windows XP Professional
root        (hd0,1)
savedefault
makeactive
chainloader    +1

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS

```You should be able to save the file and exit gedit now.

What I did is cut the lines in the code block below, then pasted to the top of the list of different kernels to run.  Then I commented out (added a # to the beginning of the lines) the business about Other Operating Systems.

If you wanted to go back to Ubuntu being the default, you could cut this line:
```

# on /dev/sda2
 title        Microsoft Windows XP Professional
 root        (hd0,1)
 savedefault
 makeactive
 chainloader    +1

```out of the top of the list, and paste it back down to the bottom of the file, remembering, for aesthetics to uncomment the lines above it:
```

# title        Other operating systems:      <---delete the "#" at the beginning
# root        <-----delete the "#" at the beginning

```or, more appropriately, assuming you've had no new kernel versions (your GRUB menu didn't get bigger), you could simply restore your backup:
```

sudo cp -f /boot/grub/menu.lst.bak /boot/grub/menu.lst

```So to sum up:
If this is confusing you, if you follow steps 1, 2, and 3 (you can just copy and paste them if you like), that should work out for you.  This way is a bit more complicated than just changing the default number (which also works), but if you want to keep it like this, even if grub gets more options on its menu (such as when you get the next version of your kernel), this way will always keep Windows on top.  Hopefully, you'll see that you boot into Ubuntu more than Windows, and you'll restore the original.

---

### Post by b21bballer on 2007-09-29
> **eph1973 said:**
> Try this out:


Step 1:
Make a backup of your menu.lst (just in case).  In your terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

I get this:

cp: cannot create regular file `/boot/grub/menu.lst.bak': Permission denied

---

### Post by b21bballer on 2007-09-29
This will be my backup:

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
# kopt=root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d9522205-9e70-414e-94dd-4d1741e0dc0c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by b21bballer on 2007-09-29
I tried to edit and got this:

Could not save the file /boot/grub/menu.lst.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

:mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by eph1973 on 2007-09-29
are you putting the sudo in front of those commands?

---

### Post by eph1973 on 2007-09-29
If you are putting the sudo in front of those commands, just to ensure you have the permissions to /boot/grub set correctly, type the following:

```
sudo chmod 0755 /boot/grub
```

---

### Post by b21bballer on 2007-09-29
Yeah, I got it. Thanks.

---

### Post by b21bballer on 2007-10-02
Anyway I can change the screen resolution?

Running 1280x800 in XP and the max in Ubuntu is 1024x768.

(Plug and Play Monitor on Mobile Intel 945GM Express Chipset Family)

---

### Post by eph1973 on 2007-10-02
Please post the results of ```
cat /etc/X11/xorg.conf | grep Modes
```

---

### Post by b21bballer on 2007-10-04
> **eph1973 said:**
> Please post the results of ```
cat /etc/X11/xorg.conf | grep Modes
```

I get:

```
                Modes           "1280x800"
                Modes           "1280x800"
                Modes           "1280x800"
                Modes           "1280x800"
                Modes           "1280x800"
                Modes           "1280x800"
```

---

### Post by b21bballer on 2007-10-04
I'm also having trouble with it recognizing my wired internet connection.

Any commands I can use to do this?

---

### Post by eph1973 on 2007-10-05
Because of the title of this thread, you may consider making two new threads.  One for your issue with the resolution, another for your issue with the wired Internet connection.  If you do this, when you make your post for the resolution issue, include the output of the following:

```
cat /etc/X11/xorg.conf
```

Also, you should include more detailed information concerning the monitor you are using:  what make and model it is, and whether it is a CRT or LCD monitor.

When you make the thread about your wired Internet connection, make sure you include the output of 
```
lspci | grep "Ethernet controller\|Network controller"
```
(That is assuming your wired Internet card is a PCI card).

---

