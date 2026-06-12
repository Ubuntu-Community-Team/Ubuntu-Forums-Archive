---
title: "Multiple + Dual Boot Problems"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by sayayinx on 2007-01-20
**I apologize before hand for making this post long.**

*Okay, here is my newbie story, please help me in any way possible, and don't give up on me.*

I decided to install Ubuntu 6.10, I already had Win XP Home edition installed.
I installed N O T the alternative CD, but the regular desktop one.

I made the partition manually when I was installing Ubuntu, and I made 1 partition, 6 Gb for linux .ext3 filesystem, and another partition for linux-swap, 400 MB. So far so good, installation went smooth, until I did a reboot.

I got the grub boot screen with no problems, linux runs great, but windows doesn't load at all.
I got a HP pavilion that has a preinstalled partition in case of emergency for windows, and the windows partition.

so, (hda1) is the emergency HP rescue... and (hda2) is the windows Ntfs partition. 
now (hda3) is the linux .ext3 partition.

The windows message that I get is autochk skipped, after that I get a reboot, and it does this forever...I have spent 2 days reading posts in this forum all over the place. So I'm going to save you all some time.

I have tried the hide / unhide partition, which doesn't work, I have tried the fixboot, fixmbr with no results, it actually made things worse. Before I did the fixmbr, I had access to my ntfs partition on the windows side, after that I lost the icon on my desktop that connected me to the hard drive.

[SIZE="3"]So I read that using umount / mount could work to load it, but this is what I get:[/SIZE]

sayayinx@sayayinx:/etc$ sudo fdisk -l

Disk /dev/hda: 40.9 GB, 40982151168 bytes
240 heads, 63 sectors/track, 5293 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         611     4619128+   2  XENIX root
/dev/hda2             612        4379    28486080   82  Linux swap / Solaris  [COLOR="Red"]<<- I have no idea why it doesn't say NTFS here!, but it is Windows XP[/COLOR]
/dev/hda3            4441        5288     6410880   83  Linux
/dev/hda4            4380        4440      461160   82  Linux swap / Solaris

Partition table entries are not in disk order
sayayinx@sayayinx:/etc$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=4a374494-f29f-40c4-95fe-ecb9706fa80c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0A56-178E  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=7EC02DB7C02D7695 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/hda4
UUID=76059065-56d2-4e9f-bc4e-9a9119b151c0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
sayayinx@sayayinx:/etc$ sudo umount /dev/hda2
umount: /dev/hda2: not mounted
sayayinx@sayayinx:/etc$ sudo mount /dev/hda2
mount: can't find /dev/hda2 in /etc/fstab or /etc/mtab
sayayinx@sayayinx:/etc$ sudo mount /media/hda2
mount: special device /dev/disk/by-uuid/7EC02DB7C02D7695 does not exist

Uhm, Thank you for reading this whole thing, I hope anyone can help me!

---

### Post by mikewhatever on 2007-01-20
I am not an expert, but try posting your GRUB menu list here
```
cat /boot/grub/menu.lst
```

On the second thought, I think this is the problem
```
/dev/hda2 612 4379 28486080 82 Linux swap / Solaris <<- I have no idea why it doesn't say NTFS here!, but it is Windows XP
```

---

### Post by Ecthelion on 2007-01-20
> /dev/hda2 612 4379 28486080 82 Linux swap / Solaris <<- I have no idea why it doesn't say NTFS here!, but it is Windows XP

Just something to check if it really IS ntfs
Install gparted (that's the tool u used to partition your disk when installingh ubuntu)
```
sudo apt-get install gparted
```
Then start up gparted
```
sudo gparted
```
Check if that hda2 is really ntfs...
If it's not recognized as one thn I think you lost all on that partition...

---

### Post by greenstar on 2007-01-20
I see that this is all on one physical disk. Win doesn't like too many primary partitions - I think Win won't handle more than 4. You have to create an extended partition to enclose the Linux partitions, which must be created as logical partitions. For more info, see here: [http://www.linuxforums.org/forum/linux-newbie/41422-there-limit-primary-partitions.html](http://www.linuxforums.org/forum/linux-newbie/41422-there-limit-primary-partitions.html)

Greenstar

---

### Post by sayayinx on 2007-01-20
[SIZE="3"]Mikewhatever: [/SIZE]here is my grub menu list:

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
timeout         20

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
# kopt=root=UUID=4a374494-f29f-40c4-95fe-ecb9706fa80c ro
# kopt_2_6=root=/dev/hda3 ro

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
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


[SIZE="3"]Ecthelion[/SIZE] I did install gparted, and I found the following:

[IMG]http://i13.photobucket.com/albums/a269/SAYAYINX/Screenshot.png[/IMG]

How can I solve this problem? Or at least save the information inside before a format or something?

[SIZE="3"]Greenstar[/SIZE]: I am lost, uhm... how do I do the extended partition? Do I have to erase everything ?

---

### Post by greenstar on 2007-01-20
I think I see part of the problem... GRUB is trying to boot your recovery partition as your Win partition. Comment out (put a # at the beginning of each line) the following section and see if it helps.

Change this:
>  # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
To look like this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
#title           Windows NT/2000/XP
#root            (hd0,0)
#savedefault
#makeactive
#chainloader     +1

The second Windows option in the *current* GRUB menu should be the correct one.

Also, do this at a terminal:
```
sudo apt-get install ntfs-progs ntfs-3g
``` This should allow gparted to properly read your ntfs partition. I think this is what it means by the Warning that is shown at the bottom of the gParted info dialog box for /dev/hda2 where it complains about a missing plugin.

Greenstar

---

### Post by rccharles on 2007-01-20
> **sayayinx said:**
> [SIZE="3"]

How can I solve this problem? Or at least save the information inside before a format or something?

[SIZE="3"]Greenstar[/SIZE]: I am lost, uhm... how do I do the extended partition? Do I have to erase everything ?

/dev/hda2 612 4379 28486080 82 Linux swap / Solaris <<- I have no idea why it doesn't say NTFS here!, but it is Windows XP

My understanding is that Windows required the correct partition type on the partition.  

I count that you have four partitions which should be good to go. Of course you are wasting some space in the unallocated space.  

You need to change the partition type on  /dev/hda2

Here is one way.  
This is an example.  I have not verified that I matches your situation.  The commands and options you use should be similar.

Be very careful...

sudo fdisk -l

# You need to find the disk name

sudo fdisk /dev/hda

# m list all options
m

# p print partition table

p

# L to list codes

L

# change the code

t
# Partition number
2

# 7 seems to be ntfs

7

# v to verify
v

# w to write to disk and quit.

w


Be carefull

Robert

---

### Post by sayayinx on 2007-01-20
[SIZE="3"]Greenstar:[/SIZE] Hey! Thanks for following my thread.

> The second Windows option in the *current* GRUB menu should be the correct one.

Also, do this at a terminal:

sudo apt-get install ntfs-progs ntfs-3g

This should allow gparted to properly read your ntfs partition. 

The sudo apt.... did not work, I get this message:

[COLOR="RoyalBlue"]sayayinx@sayayinx:~$ sudo apt-get install ntfs-progs ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done[/COLOR]
[COLOR="Red"]
E: Couldn't find package ntfs-progs
[/COLOR]

Everytime I get close to find a solution, another problem rises!

[COLOR="Black"][SIZE="3"]RCCharles:[/SIZE][/COLOR] I have no idea... could you please explain me in baby steps?

---

### Post by mikewhatever on 2007-01-20
First, can you boot into Windows or not after editing GRUB list? ntfs-progs ntfs-3g is just a driver to enable you to write to NTFS from Ubuntu.

---

### Post by sayayinx on 2007-01-20
[SIZE="3"]Mikewhatever:[/SIZE] 

>  First, can you boot into Windows or not after editing GRUB list? ntfs-progs ntfs-3g is just a driver to enable you to write to NTFS from Ubuntu. 

I cannot boot into Windows. Also, I cannot apt-get that ntfs-3g driver for some reason.

---

### Post by greenstar on 2007-01-20
I tried to combine steps to save time. Try this:
```
sudo apt-get install ntfs-3g
```
```
sudo apt-get install ntfs-progs
```

This should allow you to use gParted.

Greenstar

---

### Post by sayayinx on 2007-01-20
[SIZE="3"]Greenstar:[/SIZE] 10x 4 being so patient!

I get this error, 

```

sayayinx@sayayinx:~$ sudo apt-get install ntfs-progs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-progs
```

the ntfs-3g was installed successfully though.

---

### Post by Ecthelion on 2007-01-21
I have no idea how to solve this problem...

But what I do now is that the command should be

```
sudo apt-get install ntfsprogs
```

---

### Post by sayayinx on 2007-01-21
[SIZE="3"]Ecthelion:[/SIZE] Thank you for your help. 

I was able to download, and install it.

Now what? hehe:P

---

### Post by sayayinx on 2007-01-21
[SIZE="2"][COLOR="Blue"]Anyone care to help me?[/COLOR][/SIZE]

---

### Post by rccharles on 2007-01-21
> **sayayinx said:**
> [SIZE="3"]G

[COLOR="Black"][SIZE="3"]RCCharles:[/SIZE][/COLOR] I have no idea... could you please explain me in baby steps?

I suggest you first work on getting windows to boot. 

While you have unused space on your harddrive, I'd worry about that after you get windows to boot.

My reading of your grub menu.lst is that it displays the options to boot.  Pick the second list to boot as suggested above.



I'll add some more steps...

You first need to get into the terminal.

#Applications > accessories > terminal

# to verify that the partition number is still wrong.

sudo fdisk -l

#sudo will ask for you password.  Use your logon password.

# to see if the windows partition is mounted.

mount

# unmount the windows partition if mounted.  Notice it's umount

sudo umount /dev/hda2

# Now you are ready to use fdisk .  You need to give the name of the harddrive not a 
# partiton number

..... See my previous post.

Don't be too scared of fdisk.  Just us the m command a lot to see the options.  


Robert

---

### Post by sayayinx on 2007-01-22
[SIZE="3"]RCCharles:[/SIZE] I will try that as soon as I get home, 10x.

](*,)

---

