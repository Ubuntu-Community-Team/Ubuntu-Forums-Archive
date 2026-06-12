---
title: "GRUB:How to add my windows partition?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Hellofriends on 2007-07-02
Hello!
I just installed Ubuntu! It's awesome!
Quick question: I have a windows partiton I'd like to add to grub
it was shown at /dev/sda5 when I setting up ubuntu..but now when I boot it isnt in grubs menu @_@.
How would I add this good sirs? It is Windows XP and NTFS.


SIDE QUESTION:
Alsa does not appear to be installed or compatable
Initing OSS sound device /dev/dsp
/dev/dsp: Broken pipe
OSS: Could not toggle.

I get this when I run a program...is that an audio program yes? any suggestions? Thank you!
Thank you for your time and any help you can provide!

---

### Post by mysticrider92 on 2007-07-02
Open the Grub configuration file with: > sudo gedit /boot/grub/menu.lst
Scroll down towards the bottom, and there will be a few entries for Ubuntu. Add this at the bottom of the file: > title		Windows 
root		(hd0,4)
savedefault
makeactive
chainloader	+1
You can add it above the Ubuntu entry if you want it to boot by default. Now scroll up and look for a line like this > ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
Add a # sign in front of the word hiddenmenu at the bottom of the three lines. This will display the Grub menu at boot. 

As for the sound issue, I don't know much about that stuff in Linux (mine works out of the box and I don't mess with it).

[edit] lol, we submitted a post at the same time.

---

### Post by kittyhawk63 on 2007-07-02
Edit: sorry, I didn't notice that you had Windows on another partition of the same HDD.

Notice where I place it. This is for a separate HDD from Ubuntu.

# This entry automatically added by the Debian installer for a non-Linux OS
# on /dev/hdb1
title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

---

### Post by annda on 2007-07-02
DELETED: too late...

---

### Post by Hellofriends on 2007-07-02
It's coming up invalid..is there something I'm doing wrong?

---

### Post by kittyhawk63 on 2007-07-02
> **Hellofriends said:**
> It's coming up invalid..is there something I'm doing wrong?

Which suggestion did you use?
kh

---

### Post by Hellofriends on 2007-07-02
This is my menu.lst without any windows stuff in it. 
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
# kopt=root=UUID=08420ba7-f504-479e-9d94-01ff2f472e4d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=08420ba7-f504-479e-9d94-01ff2f472e4d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=08420ba7-f504-479e-9d94-01ff2f472e4d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Hellofriends on 2007-07-02
> **kittyhawk63 said:**
> Which suggestion did you use?
kh

Thanks for the reply.

I tried both the first one and yours. Each gave a different error.
I can see my windows partition in Ubuntu..its actually right on the desktop! Its a little drive icon
entitled 'sda5'.
I am on laptop if this has anything to do with it.
Any commands I need to type to show you more information???

---

### Post by kittyhawk63 on 2007-07-02
I don't see any reference to Windows XP? in your menu.lst. Did you remove it after it did not work?

---

### Post by mysticrider92 on 2007-07-02
What is the error you are getting? Also, the grub entry I posted was to boot Windows off of /dev/sda5 as you mentioned in your first post (Grub starts at (hd0,0) as the first partion of the first hard drive). By the way, what version of Windows are you trying to boot?

---

### Post by Hellofriends on 2007-07-02
> **kittyhawk63 said:**
> I don't see any reference to Windows XP? in your menu.lst. Did you remove it after it did not work?

yeah..I added the first suggestion right below ubuntu's after:

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

that did not work so I came back and tried yours. I deleted first suggestion and added your suggestion where his was. Each time the option showed up in grub..but failed.

---

### Post by kittyhawk63 on 2007-07-02
Check this out. Read it carefully. It will be done from boot up. I would suggest you print it.
kh

[http://ubuntuforums.org/showthread.php?p=1319395](http://ubuntuforums.org/showthread.php?p=1319395)

---

### Post by annda on 2007-07-02
this should be at the END of the file:

title Windows
root (hd0,4)
savedefault
makeactive
chainloader +1

root (hd0,4) means 5th partition of the 1st drive.

---

### Post by Hellofriends on 2007-07-02
> **mysticrider92 said:**
> What is the error you are getting? Also, the grub entry I posted was to boot Windows off of /dev/sda5 as you mentioned in your first post (Grub starts at (hd0,0) as the first partion of the first hard drive). By the way, what version of Windows are you trying to boot?

Windows XP Sp2. It is NTFS. The drive is on the desktop and says 'sda5'. Anything I can run to verify this?

---

### Post by Hellofriends on 2007-07-02
> **annda said:**
> this should be at the END of the file:

title Windows
root (hd0,4)
savedefault
makeactive
chainloader +1

root (hd0,4) means 5th partition of the 1st drive.

Invalid Device Requested

:(

---

### Post by Hellofriends on 2007-07-02
I right click and choose properties from Ubuntu desktop and goto volume it says:
MOUNT POINT:/media/sda5

Is this something important???

---

### Post by annda on 2007-07-02
this is not so great... can you post the output of

```
sudo fdisk -l
```

this will show how all the disk partitions are seen by the system.

---

### Post by Hellofriends on 2007-07-02
> **annda said:**
> this is not so great... can you post the output of

```
sudo fdisk -l
```

this will show how all the disk partitions are seen by the system.
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        4863    39062016    f  W95 Ext'd (LBA)
/dev/sda5            1825        4863    24410736    7  HPFS/NTFS
/dev/sda6               1        1580    12691255+  83  Linux
/dev/sda7            1581        1824     1959898+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2059 MB, 2059403264 bytes
38 heads, 37 sectors/track, 2860 cylinders
Units = cylinders of 1406 * 512 = 719872 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2861     2011014+   6  FAT16

```

---

### Post by kittyhawk63 on 2007-07-02
Did you try changing: hd0,5  to  hd0,4   as Mysticrider92 suggested? You have hd0,5 reserved for Ubuntu. You can't have it for both Ubuntu and Windows. That is a conflict. It will boot to the first and ignore the other. Your /dev/sda6 is for Linux. Your /dev/sda5 is for Windows.
 /dev/sda5 is shown as hd0,4 in the /boot/grub/menu.lst.

Note: hd0,0 is the first partition. The second "0" here is recognized as partition one.

If I am wrong, someone please correct me and Mysticrider92.
kh

---

### Post by annda on 2007-07-02
can you mount the win partition manually?

you need a mount point, for example /media/windows if it doesn't exist, you can create it for testing purposes like this:

```
sudo mkdir /media/windows
```

then go:

```
sudo mount /dev/sda5 /media/windows -t ntfs
```

what happens then? do you still get invalid device errors?

---

### Post by Hellofriends on 2007-07-02
> **annda said:**
> can you mount the win partition manually?

you need a mount point, for example /media/windows if it doesn't exist, you can create it for testing purposes like this:

```
sudo mkdir /media/windows
```

then go:

```
sudo mount /dev/sda5 /media/windows -t ntfs
```

what happens then? do you still get invalid device errors?

mount: /dev/sda5 already mounted or /media/windows busy
mount: according to mtab, /dev/sda5 is mounted on /media/sda5

---

### Post by Hellofriends on 2007-07-02
> **kittyhawk63 said:**
> Did you try changing: hd0,5  to  hd0,4   as Mysticrider92 suggested? You have hd0,5 reserved for Ubuntu. You can't have it for both Ubuntu and Windows. That is a conflict. It will boot to the first and ignore the other. Your /dev/sda6 is for Linux. Your /dev/sda5 is for Windows.
 /dev/sda5 is shown as hd0,4 in the /boot/grub/menu.lst.

Note: hd0,0 is the first partition. The second "0" here is recognized as partition one.

If I am wrong, someone please correct me and Mysticrider92.
kh
I tried this if that is what you mean:
title Windows
root (hd0,4)
savedefault
makeactive
chainloader +1

---

### Post by koshari on 2007-07-02
it may be worth checking the device.map file.

this file creates a partition device table and maps each partition to a grub friendly abbreviation.

example of contents of a device.map file.

> (hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/hdc
(hd3)	/dev/sda
(hd4)	/dev/sdb

---

### Post by Hellofriends on 2007-07-02
> **koshari said:**
> it may be worth checking the device.map file.

this file creates a partition device table and maps each partition to a grub friendly abbreviation.

example of contents of a device.map file.
where could I find that?

---

### Post by Hellofriends on 2007-07-02
Anyone?:cry:

---

### Post by kittyhawk63 on 2007-07-03
Check this link out, Scroll down to device.map once the page loads.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

kh

---

