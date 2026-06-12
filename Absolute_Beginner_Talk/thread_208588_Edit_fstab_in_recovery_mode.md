---
title: "Edit fstab in recovery mode"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by andybhoy.1984 on 2006-07-03
I've edited my fstab file, and made two stupid mistakes in it.  The machine is now booting into what I think is called recovery mode, and is only giving me the command line.  I already knew how to get into the fstab from here (pico /etc/fstab) and have done so, btoh logged in as myself, and as root.  Problem is, once I have fixed both silly mistakes in fstab it won't let me save it!  It says : Error writing /etc/fstab: Read-only system file

This si the stupidest thing I have ever heard of in my life, yes its an important system file, but if you can't write to it, how can you fix the obvious mistakes?  Do I have to log in as root and use chmod to make the file accessible?  My head says no, but I could be wrong.  If this is what I have to do, could someone give me the command for it please, as I'm not the cleverest at using chmod, I find the different switches confusing!

TIA

Andy
BTW: I have only been using Ubuntu for a short time, so please go easy with your replies :D

---

### Post by aysiu on 2006-07-04
Well, technically, if you're in recovery mode, you *are* root. So ```
pico /etc/fstab
``` or ```
nano /etc/fstab
``` should work.

Do you have a live CD?

---

### Post by BLTicklemonster on 2006-10-31
Edited:

I have the same problem, yet in recovery mode, I can't save. It says it's a read only file system. 

I boot to recovery and at the prompt, I type

nano /etc/fstab
(tried pico, too, and of course sudo doesn't work, either)

then make my changes, press ctrl+x, then press y, then press enter, and it won't let me save.

This is adding a hard drive that has edgy to my dapper system so I can start booting to edgy and begin moving stuff over.

All I will need to do is add a couple of #s and I'm done. Any ideas?

---

### Post by Bachstelze on 2006-10-31
Boot from a Live CD then mount your partition, like this :

```

sudo -i
mkdir /mnt/root
mount -t ext3 /dev/whatever /mnt/root
nano /mnt/root/etc/fstab
```

---

### Post by BLTicklemonster on 2006-10-31
and this will make my dapper drive where I can write to it again?

Here's my dapper fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda1 /media/hda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda5 /media/hda5 vfat rw,user,fmask=0111,dmask=0000 0 0
```

so I would put this:

```
sudo -i
mkdir /mnt/root
mount -t ext3 /dev/hda3 /mnt/root
nano /mnt/root/etc/fstab
```

right?

---

### Post by BLTicklemonster on 2006-10-31
That worked thanks. Now that I'm back in Dapper, how do I mount the drive that edgy is on?

---

### Post by BLTicklemonster on 2006-10-31
I got it now. Did you know you can edit /boot/grub/menu.lst from there, too? I didn't.

Anyway, I got it now, thanks.

---

### Post by BLTicklemonster on 2006-11-02
Okay, so that all worked, but I can't boot to dapper any more. it hangs on the splash screen. I can go to recovery, and type startx, and I get errors saying that the system 

cannot create temp file ~ read-only file system

so somehow, I have managed to get my dapper drive to be read only. How did I get here? I was testing edgy on a fresh hard drive, so I took my dapper loose while doing it. (I had good reasons) and decided I liked it, so I added it and edited the menu.lst to reflect the changes, and can boot into edgy just fine, but like I said, dapper won't let me boot to it. How can I change it to read write? Possibly something in fstab?

Dapper fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  0  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#and heeeeeres Dapper
#/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  0  
/dev/hda3                                  /media/hda3     ext3         defaults                       0  1  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                       0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0  

```

Dapper menu.lst

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
default		4

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
# kopt=root=/dev/hda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

#title		Ubuntu, kernel 2.6.15-27-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-27-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.15-27-386
#boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu, kernel 2.6.17-10-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```


Edgy fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/hdb1
UUID=a09e3c82-9a50-4582-abfc-4befba58f24c  /               reiserfs     notail                         0  1  
# /dev/hdb2
UUID=52b9e9fb-5e88-4ed6-ace9-c536086a0b4a  none            swap         sw                             0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                    0  0  
#/dev/hdd                                  /media/cdrom1   udf,iso9660  user,noauto                    0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                 0  0  
#Added by diskmounter utility
/dev/hda1                                  /media/hda1     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#Added by diskmounter utility
/dev/hda5                                  /media/hda5     vfat         rw,user,fmask=0111,dmask=0000  0  0  
#and heeeeeres Dapper
#/dev/hda3                                 /               ext3         defaults,errors=remount-ro     0  1  
/dev/hda3                                  /media/hda3     ext3         defaults                       0  0  
/dev/hda6                                  /media/hda6     swap         defaults                       0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                       0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                       0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                       0  0  

```

Edgy menu.lst

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
# kopt=root=UUID=a09e3c82-9a50-4582-abfc-4befba58f24c ro
# kopt_2_6=root=/dev/hdb1 ro

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

in case that is of any help.

---

### Post by noynac on 2007-11-05
> **andybhoy.1984 said:**
> I've edited my fstab file, and made two stupid mistakes in it.  The machine is now booting into what I think is called recovery mode, and is only giving me the command line.  I already knew how to get into the fstab from here (pico /etc/fstab) and have done so, btoh logged in as myself, and as root.  Problem is, once I have fixed both silly mistakes in fstab it won't let me save it!  It says : Error writing /etc/fstab: Read-only system file...

I ran into the same problem--I edited my fstab file and Ubuntu refused to boot (Xserver wouldn't start). I went into recovery mode and edited but could not save the fstab file because Nano reported that the file system was read only.

Is booting to a live CD and mounting the partition as described by HymnToLife the only method that can be used to edit and save the fstab file while in recovery mode?

Before editing the fstab file initially, I made a backup copy. While in recovery mode, I tried to delete the existing fstab file and rename the copy to fstab but couldn't get this to work. Is this also because the file system was read only.

The error I made in the fstab file was to the line that pertained to the Ubuntu partition. Is this the reason that the file system was read only?

As an aside, I got my computer going again by restoring the partition from a current drive image. I'm asking the above questions to better understand what happened and why. 

Thanks!

---

### Post by petteriIII on 2007-11-05
Your filesystem is corrupted. This might help:
 
[http://www.linuxsa.org.au/pipermail/linuxsa/1999-December/011333.html](http://www.linuxsa.org.au/pipermail/linuxsa/1999-December/011333.html)

---

