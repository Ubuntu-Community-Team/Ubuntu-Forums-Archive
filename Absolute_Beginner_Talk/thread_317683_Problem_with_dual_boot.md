---
title: "Problem with dual boot"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by xxlbstripesxx on 2006-12-12
I just installed ubuntu and made a 16 gig NTFS partition for windows, a 6.5 gig partition for linux, a 1.5 gig swap partition, and a 90 or so gig FAT32 partition. When I load my computer it does not give me any option to boot into windows and when I look at the partitions on my drive it views the NAT32 and NTFS drives as unknown. I was wondering both what happened and wondering what i need to do to fix this.And when I start my computer it does not give me the optione to boot into Windows

---

### Post by bodhi.zazen on 2006-12-12
Post /boot/grub/menu.lst for boot issues.

As far as your ntfs and vfat partitions:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by xxlbstripesxx on 2006-12-12
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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by xxlbstripesxx on 2006-12-12
Whenever I use sudo nano /etc/fstab I do not see the NTFS file I only see: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

Whenever i use fdisk-l I see:
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         892     7164958+  83  Linux
/dev/hda2             893        3060    17414460    7  HPFS/NTFS
/dev/hda3            3061        3251     1534207+  82  Linux swap / Solaris
/dev/hda4            3252       14593    91104615    b  W95 FAT32

---

### Post by bodhi.zazen on 2006-12-12
To list your partitions: ```
sudo fdisk -l
```

---

### Post by bodhi.zazen on 2006-12-12
To boot windows you need to add an entry for windows in grub.

```
gksudo gedit /boot/grub/menu.lst
```

Add this entry last (After title Ubuntu, memtest86+ .... )

> title Windows XP
root (hd0,1)
makeactive
chainloader +1
savedefault
boot

Save and exit your editor.

Reboot and you should be good to go ....

---

### Post by xxlbstripesxx on 2006-12-12
I edited my grub and it now looks like this:

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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title Windows XP
root (hd0,1)
makeactive
chainloader +1
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

It still boots directly to Ubuntu.

---

### Post by Thendin on 2006-12-12
You seem to have the hiddenmenu command enabled have you tried pressing escape to show the boot menu?

---

### Post by xxlbstripesxx on 2006-12-12
Thank you i tried it and when i selected windows XP it gave me this:
Error 13 : invalid or unsupported .exe format

---

### Post by xxlbstripesxx on 2006-12-13
Also why does it show my NTFS and FAT32 drives as inaccessible

---

### Post by bodhi.zazen on 2006-12-13
Don't know about your error 13 :(

See  my first post re mounting your FAT and NTFS partitions. :)

---

### Post by xxlbstripesxx on 2006-12-13
I tried but when I used the command : sudo nano /etc/fstab I only get

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

It doesn't show the NTFS or FAT32 drives which are hda2 and hda4 respectively. However it shows them when I use fdisk-l everything in the tutorial in the link works correctly except for this step I mount them again and it doesn't work. Any suggestions?

---

### Post by bodhi.zazen on 2006-12-13
> **xxlbstripesxx said:**
> I tried but when I used the command : sudo nano /etc/fstab I only get

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

It doesn't show the NTFS or FAT32 drives which are hda2 and hda4 respectively. However it shows them when I use fdisk-l everything in the tutorial in the link works correctly except for this step I mount them again and it doesn't work. Any suggestions?

What are you mount points ?

You need to make them, this is how:
```
sudo mkdir /mnt/FAT
sudo mkdir /media/NTFS
```

Call the mount points what you will. Make them in /media if you want them on your desktop, otherwise put them in /mnt.

Now your fstab enteries:
> /dev/hda2 /media/NTFS ntfs users,defaults 0 0
/dev/hda4 /mnt/FAT vfat auto,users,umask=000 0 0

They should now mount at boot.

To mount:
```
mount /media/NTFS
mount /mnt/FAT
```

Your ntfs will be ro. for rw see: 
[http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

---

### Post by xxlbstripesxx on 2006-12-13
I made the directories and put in the fstab entries as such.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2 /media/NTFS ntfs users,defaults 0 0
/dev/hda3       none            swap    sw              0       0
/dev/hda4 /mnt/FAT vfat auto,users,umask=000 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0



when i enter the mount command i get the following error for both drives:



mount: wrong fs type, bad option, bad superblock on /dev/hda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by xxlbstripesxx on 2006-12-13
I just looked at my disks manager in Ubuntu this morning and under the partitions it says File System: Windows NTFS and Access Path: /windows
and for parition 4 it says File System: Windows Virtual FAT access path /mnt/FAT and on both it says free space not available and I still have the error 13 and mount errors

---

### Post by xxlbstripesxx on 2006-12-13
I looked in my syslog and found this what does it mean?

[17179594.072000] NTFS-fs warning (device hda2): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179594.072000] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179594.072000] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179594.072000] NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.
[17179594.092000] FAT: bogus number of reserved sectors
[17179594.092000] VFS: Can't find a valid FAT filesystem on dev hda4.

also what do these mean:

[17179570.108000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.108000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.108000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.108000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.108000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.108000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.108000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.108000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.108000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[17179570.124000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0

I also ran fsck on my drives and this is what I got for each of them:

chris@chris-laptop:~$ fsck /dev/hda2
fsck 1.38 (30-Jun-2005)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/hda2
chris@chris-laptop:~$ fsck /dev/hda4
fsck 1.38 (30-Jun-2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/hda4:Permission denied

---

### Post by xxlbstripesxx on 2006-12-16
Can someone please help me I have no clue what to do.

---

