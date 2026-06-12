---
title: "Dual Booting OS X and Ubuntu"
date: 2007-03-11
forum: Apple PPC Users
---

### Post by fight4theright on 2007-03-11
Hello all!

I have a PPC Mini, and want to install Ubuntu on the blank internal drive. 

Right now I boot OS X off of an external 250GB firewire drive, and would like to leave it there, and use the internal for Linux.

My question is how to make the bootloader recognize my firewire drive, and the operating system contained on it?

---

### Post by fight4theright on 2007-03-16
Bump!

All I really need is the 'path' to the external drive. Does anyone know that?

---

### Post by rccharles on 2007-03-16
> **fight4theright said:**
> Bump!

All I really need is the 'path' to the external drive. Does anyone know that?

What I do is hold down the option ( or alt on a pc keyboard ) when I power on my machine.  This brings up the Mac boot manager.  It will show you all the bootable partitions.

Robert

---

### Post by fight4theright on 2007-03-18
Yea, that works, although it takes quite a while before I am able to click on a volume. I was wondering if there was a faster way?

---

### Post by seatea on 2007-03-19
Editing yaboot.conf will give a faster way by  using yaboot to boot your systems. There are several websites that can offer assistance. Start here, [HTML]http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml[/HTML], then do a google search for ubuntu boot off external drive. It often takes some trial and error to get things  set up right.

---

### Post by fight4theright on 2007-03-22
> **seatea said:**
> Editing yaboot.conf will give a faster way by  using yaboot to boot your systems. There are several websites that can offer assistance. Start here, [HTML]http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml[/HTML], then do a google search for ubuntu boot off external drive. It often takes some trial and error to get things  set up right.

No ****. I need to know the path to the external drive.

---

### Post by grazie on 2007-03-22
Well that's easy enough
```
$ ofpath <external device>
```

---

### Post by seatea on 2007-03-23
The link  I put in my post takes you to a section in the yaboot how to on finding the open firmware path.

---

### Post by pxwpxw on 2007-03-24
fight4theright:

In an ibookg4 (2005) the Open Firmware path for a single external
hard drive, firewire connection is
	
	fw/node/sbp-2/disk:

If the mini is a Applemac not an intel, it might use the same path

That might work assuming macosx is the first bootable on the external.

If not, then try
 
	fw/node/sbp-2/disk:X

where X is the macosx partition number on the external.


grazie:

The ofpath utility I have in edgy returns 
"sg is not supported" for external firewire 
"usb-storage is not supported" for exterrnal usb.

Would certainly save a lot of problems if it did support firewire drives, when ofpath is consulted by ybin/mkofboot when setting up the yaboot bootstrap. 

seatea:

I looked at the  link which is good for local drives, but external firewire 
O/F paths are something else.

---

### Post by grazie on 2007-03-24
> **pxwpxw said:**
> 
The ofpath utility I have in edgy returns 
"sg is not supported" for external firewire 
"usb-storage is not supported" for exterrnal usb.

Would certainly save a lot of problems if it did support firewire drives, when ofpath is consulted by ybin/mkofboot when setting up the yaboot bootstrap. 


I guess I should have checked that before posting. No doubt that's the reason Ubiquiity fails to install yaboot on Firewire and USB drives during an installation.

Edit
```
$ echo /proc/device-tree/pci*/firewire*/node*/sbp-2*
```
The above seems to be one a way to determine the ofpath of the firewire device (Works for me)

---

### Post by pxwpxw on 2007-03-24
**grazie**

Yes, thanks. Better than trying to find paths using open firmware.

It would be good if someone wrote a script to extract paths ending with disk*
from /proc/device-tree/ - could provide a more general solution.

Heres how my powermacG5 sees it (debian etch ) for an external firewire hard disk (icecube/wdc160).

```

$ echo /proc/device-tree/ht*/pci*/firewire*/node*/sbp-2*/disk*/

/proc/device-tree/ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0/


```

Probably the path could be abbreviated:
 
	/ht/pci@5/firewire/node/sbp-2/disk:


and for 2 internal sata drives: ( but there are aliases sd0: and sd1: for those).

```

$ echo /proc/device-tree/ht*/pci*/k2*/k2*/disk*/

/proc/device-tree/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0/

/proc/device-tree/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0/

```

---

### Post by seatea on 2007-03-24
If you have linux installed on your mac-mini, in terminal type "sudo fdisk -l". This  should print out  device numbers  for the partitions  on the  firewire and hard drive. It probably will be something  like /dev/sdax and /dev/hda where "x" is a number. sda numbers usually  are for your firewire. That is what you need to find the ofpath  to. Here are a couple of links I  found useful, [http://hansmi.ch/articles/boot-linux-from-firewire](http://hansmi.ch/articles/boot-linux-from-firewire) and [http://macubuntu.blogspot.com](http://macubuntu.blogspot.com). You are trying to boot OS X instead of linux on the firewire, but the technique should be similar. You might need to add enableofboot in your yaboot.conf. You also will need to  add something  like macosx=/dev/sdax (again x is the number for your Mac OS X partition). You might even need to type out the  whole open firmware path to  you mac x partiton). It  will  look  something like macosx=/pci@f2000000/pci-bridge@d/firewire@a/node@00d0b87c455b37df/sbp-2@0:X(again X is the number for your Mac OS X partition).

Here's a sample yaboot.conf that boots ubuntu  off firewire.

> ## yaboot.conf
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.

fgcolor=yellow
bgcolor=black

boot=/dev/sda7
ofboot=/pci@f4000000/firewire@e/node@0010b9210040ad70/sbp-2@c000/disk@0:7
device=/pci@f4000000/firewire@e/node@0010b9210040ad70/sbp-2@c000/disk@0:3
partition=3
delay=15
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macos=/dev/hda14
macosx=/dev/hda9
brokenosx

image=/boot/vmlinux
	label=Linux
	read-only
	root=8:3
	append="rootdelay=10"



# To boot a different installation (for example on an IDE drive partition 12)
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12,/vmlinux
    label=hda12-Linux
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:12
    append="root=/dev/hda12 ro"


---

### Post by pxwpxw on 2007-03-25
Good links **seatea**, it is possible to do it a bit simpler though:

Posting this from xubuntu610 running on an external 160GB firewire drive
on a powermacG5 which also has 2 hard drives, MacosX, and 2 debian installations.

This external xubuntu system was booted by yaboot on sda2 (one powermac hard disk)
The yaboot bootstrap sda2 was written from a debian installation on sda4.

An abbreviated openfirmware path can be used in yaboot.conf
for the xubuntu image. The "fw" is an alias which takes care of actual 
path differences to the firewire nodes between some NewWorld Apple Macs.

```

## yaboot.conf 
## test version includes image to boot external firewire ubuntu610
## 
boot=/dev/sda2
ofboot=sd0:2
device=sd0:
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=sd1:3

image=/boot/vmlinux
	root=/dev/sda4
	label=db1
	read-only
	initrd=/boot/initrd.img
partition=4

image=/boot/vmlinux
	root=/dev/sda7
	label=db2
	read-only
	initrd=/boot/initrd.img
partition=7

## ubuntu610 on external firewire disk
image=/boot/vmlinux
	root=/dev/sdc6
	label=exfw
	read-only
	initrd=/boot/initrd.img
partition=6
device=fw/node/sbp-2/disk:

image=nothing
    label=dontdothis
    
  

```

In the external firewire drive (sdc) partition map 
xubuntu root is sdc6, home is sdc8, swap sdc9. The other partitions are
from other tests and not relevant here.

> 
/dev/sdc
        #                    type name                  length   base      ( size )  system
/dev/sdc1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sdc2         Apple_Bootstrap uboot                 262144 @ 64        (128.0M)  NewWorld bootblock
/dev/sdc3               Apple_HFS Apple_HFS_Untitled_1  77883312 @ 262208    ( 37.1G)  HFS
/dev/sdc4         Apple_Bootstrap ubx2                  262144 @ 78145520  (128.0M)  NewWorld bootblock
/dev/sdc5               Apple_HFS Apple_HFS_Untitled_2  77883312 @ 78407664  ( 37.1G)  HFS
/dev/sdc6         Apple_UNIX_SVR2 ubu610root          19531251 @ 234436432 (  9.3G)  Linux native
/dev/sdc7               Apple_HFS Apple_HFS_Untitled_3  77883312 @ 156553120 ( 37.1G)  HFS
/dev/sdc8         Apple_UNIX_SVR2 ubu610home          39062501 @ 253967683 ( 18.6G)  Linux native
/dev/sdc9         Apple_UNIX_SVR2 swap                 3906251 @ 293030184 (  1.9G)  Linux swap
/dev/sdc10        Apple_UNIX_SVR2 u610extra           15645373 @ 296936435 (  7.5G)  Linux native
/dev/sdc11             Apple_Free Extra                 262144 @ 156290976 (128.0M)  Free space

Block size=512, Number of Blocks=312581808
DeviceType=0x0, DeviceId=0x0


---

