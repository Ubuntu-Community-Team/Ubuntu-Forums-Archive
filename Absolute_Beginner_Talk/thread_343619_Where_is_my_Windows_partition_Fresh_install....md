---
title: "Where is my Windows partition? Fresh install..."
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by BOBSONATOR on 2007-01-21
Hey guys, I just installed edgy and fgrlx

Previously i had a 80gig hd that was all windows but was 56gb full, so i resized that partition to 57gigs left 18 gigs for ubuntu, and 2 gig swap.

I install ubuntu and everything works fine, i just cant see my windows partition, (It should be on my desktop,) But i cant find it.

Thanks for help.

---

### Post by Shatrat on 2007-01-21
You need to add it to your /etc/fstab (filesystem table)
Mine looks like this ```
/dev/hda1                                  /mnt/windows    ntfs         nls=utf8,umask=0222  
```

If you really want it on your desktop change the mount point from /mnt/windows to /media/windows , but I find that annoying.
the /dev/hda1 might not be the right device for you, you can see what partitions are on your computer using the ```
cat /proc/partitions
```  You'll probably be able to recognize it by the number of blocks since its the largest one.  There's probably an easier way to identify it but I can't think of it right now.

---

### Post by BOBSONATOR on 2007-01-21
This is my output 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ecf1a4c5-2b07-4e52-a50d-5fa01242ae3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=0509f9e4-1446-4e2a-a39f-787e4369d99b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


and this 

> major minor  #blocks  name

   8     0   78125000 sda
   8     1   59689476 sda1
   8     2   16338105 sda2
   8     3    2096482 sda3
shayan@shayan-desktop:~$ 




---

### Post by taurus on 2007-01-21
```
sudo fdisk -l
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by BOBSONATOR on 2007-01-21
Thanks taurs, i configured it like this, but i still dont see it, and i when i select Windows XP Pro @ the grub list, it says starting up and hangs there..


Here is my new fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1                                  /mnt/windows    ntfs         nls=utf8,umask=0222
# /dev/sda2
UUID=ecf1a4c5-2b07-4e52-a50d-5fa01242ae3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=0509f9e4-1446-4e2a-a39f-787e4369d99b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



---

### Post by taurus on 2007-01-21
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by BOBSONATOR on 2007-01-21
> **taurus said:**
> Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7431    59689476    7  HPFS/NTFS
/dev/sda2            7432        9465    16338105   83  Linux
/dev/sda3            9466        9726     2096482+  82  Linux swap / Solaris

```

---

### Post by taurus on 2007-01-21
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Create a mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

### Post by meng on 2007-01-21
Your Windows partition is /dev/sda1
EDIT: way too slow!

---

### Post by BOBSONATOR on 2007-01-21
Ok did all of that, but i still cant see my partition or boot into it from grub.

I appriciate your help taurus

---

### Post by taurus on 2007-01-21
Wait a second.  I think we are talking about two different things here.  Do you want to add Windows to the GRUB menu so you can boot your XP?  Or do you want to mount your Windows in Ubuntu so you can access files there?

---

### Post by jonny on 2007-01-21
> **BOBSONATOR said:**
> Hey guys, I just installed edgy and fgrlx

Previously i had a 80gig hd that was all windows but was 56gb full, so i resized that partition to 57gigs left 18 gigs for ubuntu, and 2 gig swap.

I install ubuntu and everything works fine, i just cant see my windows partition, (It should be on my desktop,) But i cant find it.

Thanks for help.

If you followed Taurus' instructions, you should be able to see your Windows partition by navigating to /media/sda1.  You won't necessarily see it on uyour desktop.

This issue stumbles newcomers to Ubuntu, but there are very good security reasons for the default settings.  Linux doesn't observe Windows security settings, so, if you mount your Windows partition to your desktop, you should be aware that any user of your PC will be able to access any file on your Windows partition.  That might not be such a smart idea if your PC is shared.

---

### Post by BOBSONATOR on 2007-01-21
> **taurus said:**
> Wait a second.  I think we are talking about two different things here.  Do you want to add Windows to the GRUB menu so you can boot your XP?  Or do you want to mount your Windows in Ubuntu so you can access files there?

All i want is to see my windows partition from Ubuntu, and boot XP from grub (It is on the grub list, just doesnt boot)

Here is a screen of my thing..

---

### Post by taurus on 2007-01-21
What's the output of this command?

```
df -h
```

---

### Post by BOBSONATOR on 2007-01-21
> **taurus said:**
> What's the output of this command?

```
df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              16G  2.2G   13G  15% /
varrun                506M   84K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                506M   24K  506M   1% /dev/shm
lrm                   506M   17M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1              57G   57G  507M 100% /windows

```

---

### Post by taurus on 2007-01-21
> **BOBSONATOR said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              16G  2.2G   13G  15% /
varrun                506M   84K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                506M   24K  506M   1% /dev/shm
lrm                   506M   17M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1              57G   57G  507M 100% /windows

```

Apparently, you mounted /dev/sda1 to /windows instead of /media/sda1 so you need to look in /windows.  And looks like that thing is filled up to capacity.

---

### Post by BOBSONATOR on 2007-01-21
Oh thanks a bunch, i just did CNTRL+L and searched windows.

Now i just need it to boot from grub, (the entry is already there)

---

### Post by meng on 2007-01-21
Please show us your menu.lst:

cat /boot/grub/menu.lst

---

### Post by BOBSONATOR on 2007-01-21
Here you go (You guys rock)

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=ecf1a4c5-2b07-4e52-a50d-5fa01242ae3e ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


---

### Post by BOBSONATOR on 2007-01-21
Any help?

PS: The sda1 Icon is on my desk, and i cant remove it.

---

### Post by taurus on 2007-01-21
```
sudo rmdir /media/sda1
```

---

