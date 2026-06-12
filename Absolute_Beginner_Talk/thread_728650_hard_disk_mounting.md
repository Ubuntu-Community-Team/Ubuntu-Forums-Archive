---
title: "hard disk mounting"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by amit.padhy on 2008-03-19
Hi all
I am a newbie to ubuntu.(7.10)

when i do a fdisk -l ,i get the following:

Code:

root@amit:/home/amit# fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40764075

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4665    37471581   83  Linux
/dev/sda2            4666        4870     1646662+   5  Extended
/dev/sda5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002c002c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17026   136751909+   f  W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sdb2           17026       17090      514080    2  XENIX root
Partition 2 does not end on cylinder boundary.
/dev/sdb3           17090       18413    10625594+   3  XENIX usr
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *       18414       19456     8377897+   7  HPFS/NTFS
root@amit:/home/amit# 

what is this : W95 ext'd (lba) and xenix root/usr
i mean how do i mount these filesystems on ubuntu(if i can???)

the problem is i cannot view them through windows either...
Can anybody please help??

Thanks

---

### Post by Xiong Chiamiov on 2008-03-19
[Xenix]("http://en.wikipedia.org/wiki/Xenix"), but f w95 I do not know (though w95 sounds sneakily like windows 95 to me).  How did you end up with these things?

---

### Post by Kiri on 2008-03-19
They might be just hidden recovery partitions on your computer. Unless you know they have some files you need, I wouldn't worry about them.

---

### Post by cm.squared on 2008-03-19
Hi there,

fdisk -l prints your partition scheme, so what your seeing is the partitions you have on your two hard drives.  sda is your first hd, sdb is your second.

The numbers following sda and sdb are the partitions on those hard drives.  I'm pretty sure that win95 ext'd is some sort of extended partition.  On a hard disk with an msdos disk label you can only have 4 primary partitions, so you make up for that with extended partitions, which act like a box in which you can put logical partitions so you can get past the 4 partition limit imposed by an msdos disk label.  That's only a cursory explanation of partitions, so if you're looking for more you might read this article: [The how and why of partitioning]("http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html").  Googling linux partitioning should also return some informative articles.

To see what's on those partitions, you would use the mount command, of the general format:
```
sudo mount -o [ro|rw] [device] [directory]
```
and more specifically for you:
```
sudo mount -o ro /dev/sdb2 <some-folder>
```

What this will do is attach /dev/sdb2, the second partition on the second hd labelled xenix root, to the directory <some-folder>.  You will want to create a folder, in your home directory called "mount" for example, before issuing the command.  Once the device is mounted, you can navigate through it as if it were a regular directory.  You can repeat this process with the rest of the partitions in question.  For more info on mounting, see [Mounting]("http://www.tuxfiles.org/linuxhelp/mounting.html").

Hope this helps.  Please ask for clarification if any of this is hazy.  Everything about mounting and partitions is a lot of information to absorb at once.

::Edit:: the options ro and rw are for mounting read only and read write, respectively, so at first you might mount read only if you're just browsing throught the contents of the partition.

---

### Post by cm.squared on 2008-03-19
Also, to umount a device from a directory, you use the umount command:
```
sudo umount [device]
```

so you'll need to unmount sdb2 from <some-directory> before you mount another device to it.
```
sudo umount /dev/sdb2
```

Note that the command is umount, and not unmount.

---

### Post by amit.padhy on 2008-03-19
a week back my windows(xp) and ubuntu 7.04 had some problems..
basically crashed..

windows was on my 40 gb hard disk and most of 160GB HD was under windows with some 15 GB on linux....

i installed new OSs....windows  on 8GB of 160 GB...and linux on the 40GB HD...

so this sdb1 i think was the windows partition on 160 GB HD....
but now i can't see the filesystem...

I have moderately important data on this system

Btw,there was a grub error on my ubuntu(21 and 17)
and login error on windows(registry mess) 
coz of which i installed OSs....

---

### Post by cm.squared on 2008-03-19
Let me see if I understand what's happened:

You had windows on your first partition, and a windows partition and a linux partition on your second.

Both of those crashed, so you reinstalled them, but this time windows on the second and linux on the first.

Now you can't see your old windows partition, and grub gives you errors.

If that's the situation, I have a couple of questions:
1. What works and what doesn't?  Can you boot into either os?
2. When do you get errors from grub?
3. Did you do any repartitioning, like with the ubuntu livecd, when your reinstalled the operating systems? or did you reinstall them on your existing partitions?

---

### Post by cm.squared on 2008-03-19
Posting copies of your /etc/fstab and /boot/grub/menu.lst files would also probably help in diagnosing some of your problems.  Your can make these by entering the following into your terminal:
```
sudo cat /etc/fstab
```
and
```
sudo cat /boot/grub/menu.lst
```

---

### Post by amit.padhy on 2008-03-20
[PHP]
This is what I get:
[/PHP]

---

### Post by amit.padhy on 2008-03-20
This is the output of fdisk -l  :


```

root@amit:/home/amit# fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40764075

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4665    37471581   83  Linux
/dev/sda2            4666        4870     1646662+   5  Extended
/dev/sda5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002c002c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17026   136751909+   f  W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sdb2           17026       17090      514080    2  XENIX root
Partition 2 does not end on cylinder boundary.
/dev/sdb3           17090       18413    10625594+   3  XENIX usr
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *       18414       19456     8377897+   7  HPFS/NTFS
root@amit:/home/amit# 


```


and the /etc/fstab cantains the following:

```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=7a75ace6-8fad-4aac-9173-0073d75a6316 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=4d529a96-8320-44a7-9102-13868090e188 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sdb4 /media/sdb4 ntfs-3g defaults,locale=en_US.utf8 0 0

```

this is the /boot/grub/menu.lst

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
# kopt=root=UUID=7a75ace6-8fad-4aac-9173-0073d75a6316 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a75ace6-8fad-4aac-9173-0073d75a6316 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a75ace6-8fad-4aac-9173-0073d75a6316 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Basically, the 136GB or sdb1 was my extended partition on my earlier windows....
now that my windows has been removed,can i accesss the data in this extended partition by any means?????????

---

### Post by amit.padhy on 2008-03-20
The problem was with the earlier OSes...
now that i have installed new ones...i can boot into either

i installed linux on the 40 gb HD which got formatted...

but in the 160GB HD,only one of the partitions was formatted....
the extended partition wasn't formatted.......i am not sure if while installation it got formatted without asking me....

when i try to mount it asks to enter a valid file system...i.e  its neither ntfs nor fat32...

---

### Post by cm.squared on 2008-04-03
To access sdb1 try using this command:

```
sudo mount -o rw,auto /dev/sdb1 <mount-folder> 
```

The "-o rw,auto" option will mount the filesystem read/write and should autodetect the type. 

You'll want to replace <mount-folder> with an empty folder that you've created to use as a mount point.  You can then navigate through sdb1 by opening <mount-folder> as you would any other folder.

Once your done looking you will unmount the device with the following command:

```
sudo umount /dev/sdb1
```

You can replace /dev/sdb1 with any other device to repeat the process and browse throught the rest of your partitions.

---

