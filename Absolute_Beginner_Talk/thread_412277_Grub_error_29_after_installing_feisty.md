---
title: "Grub error 29 after installing feisty"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by CFMV on 2007-04-17
Ok, i installed feisty with 2 IDE drives connected a master with some windows data and a slave wich was my feisty destination after all installation is done i get error 29: disk write error.

After some testing i disconnected my master drive and only left connected the slave one, feisty installs perfectly and runs like its supposed to be. Then i go and connect my master drive, i dunno if its supposed to change, but my bios booting order changes making the master drive boot first, i go and change it back so my ubuntu drive boots first and then BAMMM i get the same error Grub error 29. I even tried to edit where the grub searches for the linux booting files, changing it from (hd0,0) to (hd1,0) but nada, didnt work got another Grub error, think it was error 17: cannot mount selected partition.

The weird thing is that i'm able to load Feisty, selecting recovery mode and then gdm to load gnome.

I even tried changing my slave-linux drive to master and my master-windows drive to slave and nada, same error 29.

I'm out of ideas now. Here are my menu.lst and fdisk -l files:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3647    29294496    7  HPFS/NTFS
/dev/hda2   *        3648        7296    29310592+   b  W95 FAT32
/dev/hda3            7297       14592    58605120    f  W95 Ext'd (LBA)
/dev/hda5            7297       14592    58605088+   7  HPFS/NTFS

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       10011    80164350    5  Extended
/dev/hdb5              32       10011    80164318+  8e  Linux LVM



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
# kopt=root=/dev/mapper/cmodem--233--196-root ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/cmodem--233--196-root ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/cmodem--233--196-root ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-12-generic root=/dev/mapper/cmodem--233--196-root ro quiet splash
initrd		/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-12-generic root=/dev/mapper/cmodem--233--196-root ro single
initrd		/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Sorry for the long post and thanks in advance for your help.

---

### Post by leibowitz on 2007-04-18
Could you please post the output of the second command. You need to run linux and be logged in to do this.
```
sudo grub
find /boot/grub/stage1
```

---

### Post by CFMV on 2007-04-18
```
grub> find /boot/grub/stage1

Error 15: File not found
```

---

### Post by leibowitz on 2007-04-19
EDIT: please try with the installation CD first, if I remember correctly there is a boot entry that can recover the boot menu for you. 

Ok, can you please try this:
Change the first occurance of (hd0,0) to (hd0,2)

This is in here
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,[COLOR="Red"]2[/COLOR])
kernel /vmlinuz-2.6.20-15-generic root=/dev/mapper/cmodem--233--196-root ro quiet splash
initrd /initrd.img-2.6.20-15-generic
quiet
savedefault
```

Also, there is "root=/dev/mapper/cmodem--233--196-roo" that seems to be weird. May be related to the LVM volume, I don't know what it means.

In fact I'm sure of one thing. If you connect all your disks (both IDE and one SATA drive) then your (hd0,x) configuration will be one of : hd0,1 or hd0,2 

It will be hd0,1 if the IDE drives are listed before the SATA in the GRUB program. And I don't know how GRUB handles this situation as I don't faced it yet.

If the SATA is in fact recognised first, then hd0,0 will point to the SATA drive. So your slave IDE (with linux) will be (hd0,2).


I think you did have it right with hd0,1 and the mount error was related to the root=/dev/mapper/cmodem--233--196-roo

So try changing that to root=/dev/hdb1 aswell

Final Result is
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,2)
kernel /vmlinuz-2.6.20-15-generic root=[COLOR="Red"]/dev/hdb1[/COLOR] ro quiet splash
initrd /initrd.img-2.6.20-15-generic
quiet
savedefault
```

PS: You don't have to reboot each time to test this. Just edit your grub configuration on the fly, using the "E" key in grub to edit an entry. Then Pressing "e" again will allow you to edit line per line in this entry. Then press "enter" to validate your changes, and "b" to boot this entry with the changes applyed. Don't press "ESC" or you will drop your changes...

PSS: this is just a way of testing new configurations. You still have to edit the /boot/grub/menu.lst at the final step to store your changes by hand.

---

### Post by richardgundersen on 2007-04-20
Just wanted to say thanks for the tip you gave the last poster. I was actually getting error 17 from grub, but after using your tips and a bit of trial and error i finally managed to get my dual boot up and running. 

Bit of a shame that FF didnt work off the cd for me when Edgy was fine though.

---

### Post by richardgundersen on 2007-04-20
Quick question - pressing b doesnt seem to save the settings. I have to change it each time I restart my pc. Any ideas?

---

### Post by leibowitz on 2007-04-20
That's the current documented behavior. Pressing 'b' will just boot the current edited configuration. But it cannot be saved. You need to edit the /boot/grub/menu.lst file by hand (with sudo) and save it. Do it when you are on Linux.

---

