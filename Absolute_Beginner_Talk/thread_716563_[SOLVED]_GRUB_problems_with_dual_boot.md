---
title: "[SOLVED] GRUB problems with dual boot"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by FrozenFlame22 on 2008-03-06
I dual boot Ubuntu Gutsy Gibbon and Windows XP on two seperate SATA hard drives (computer also contains several other non booting IDE hard drives connected via PCI expansion card). With the most recent kernal update, my GRUB was overwritten and I can't for the life of me remember how I got dual booting to work in the first place. Some pointers in the right direction please?

fdisk -l
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02cc02cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241   83  Linux

Disk /dev/sdb: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19e019df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1868    15004678+  83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c002b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29765   239087331   83  Linux
/dev/sdc2           29766       30515     6024375    5  Extended
/dev/sdc5           29766       30515     6024343+  82  Linux swap / Solaris

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4adf4adf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9728    78140128+   7  HPFS/NTFS

```

menu.lst
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
# kopt=root=UUID=0c27d207-775e-4c1a-87d9-c194e8af08cb ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0c27d207-775e-4c1a-87d9-c194e8af08cb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0c27d207-775e-4c1a-87d9-c194e8af08cb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0c27d207-775e-4c1a-87d9-c194e8af08cb ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0c27d207-775e-4c1a-87d9-c194e8af08cb ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I've tried a few things such as:

title		Windows XP Home
root		(hd4,0)

but these only result in a "Error 21".

---

### Post by thisiam on 2008-03-06
title		Microsoft Windows XP
root		(hd4,0)
savedefault
makeactive
chainloader	+1

---

### Post by FrozenFlame22 on 2008-03-06
> **thisiam said:**
> title		Microsoft Windows XP
root		(hd4,0)
savedefault
makeactive
chainloader	+1

Thanks for replying! I tried this just now, copied and pasted even, but it didn't work. I got the "Error 21: Selected disk does not exist" again.

---

### Post by Kiri on 2008-03-06
I think you need to write (hd3,0) because it starts counting from zero... 
so even though its disk 4, it starts from 0, so it should be disk 3 if you follow me.

---

### Post by thisiam on 2008-03-06
i haven't got this error myself yet so i haven't read to much but from reading now i found this [http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)
i would go from there.

---

### Post by FrozenFlame22 on 2008-03-06
I burned a Super Grub disk and I'm fiddling around with it. It's getting pretty late in my time zone so I might have to come back to this tomorrow. I'll post the results then. Thanks again for the suggestion!

---

### Post by hansonwe on 2008-03-06
Here's my "trial and error" experience,which someone may find helpful ...
My system:
Master: WD 320 GB SATA (sda) (NTFS: Windows XP Pro)
Slave: WD 120 GB SATA (sdb) (Ubuntu - 4 partitions: swap, /, a FAT32 share, and /home)
Seagate 500 GB SATA (sdc) (NTFS)

First 2 drives are connected to the motherboard, the 3rd is via a add-on SATA card.  
To keep my WinXP disk pristine (my dissertation research is on it), I disconnected the two NTFS drives before installing Ubuntu (so the Grub bootloader is on the Slave drive) , and then switched the boot order in the BIOS to boot directly from the slave.  That way nothing messes with the MBR on my primary WinXP drive.  

So, I manually edited the grub menu (sudo gedit /boot/grub/menu.lst) to add the WinXP boot section.  My first attempt was ...
[INDENT]
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=23551dc4-a198-499d-9bb0-f2ed1db98195 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

(other entries snipped to save space)

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP Professional
rootnoverify	(hd1,1)
makeactive
chainloader	+1[/INDENT]

That combination allowed me to boot into Ubuntu no problem, but trying windows gave an "error 22 - no such partition" message.  

So, I tried again with another partition (showing the WinXP section only):  

[INDENT]title		Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1[/INDENT]

This caused the computer to display the "Starting up ..." message, then then the machine hangs.  
At this point, I was wondering if I was pointed to the wrong disk.  fdisk -l gave conflicting results each time ... sometimes would list the disks in order above, sometimes the order would reverse, so maybe booting from the slave was confusing it.  Not being sure if that was a bug or a feature, I tried:

[INDENT]title		Windows XP Professional
rootnoverify	(hd2,0)
savedefault
makeactive
chainloader	+1[/INDENT]

Which got me the same result:  "Starting up ..." then hangs

At that point, I decided to read the directions and went to the GNU Grub manual.  While it doesn't address my situation completely, it did suggest using the "map" command to swap drives.  
I tried this set of commands, and it worked like a champ:

[INDENT]title		Windows XP Professional
map		(hd0) (hd1)
map		(hd1) (hd0)
root		(hd1,0)
savedefault
makeactive
chainloader	+1[/INDENT]

Now I can dual boot without problems, and both WinXP and Ubuntu drives are totally self-contained, so that failure on one side will not affect the other, nor are there any modifications to the WinXP MBR.  

As always, YMMV but I hope that someone finds my learning process helpful.  
Cheers,
- Bill H

---

### Post by FrozenFlame22 on 2008-03-06
I'm still not quite hitting on a solution. As long as I have the Super Grub disk in my computer at reboot, I am able to boot into Windows XP, which bypasses GRUB all together. This is a quick fix, but not a solution. However it does tell me that the Windows drive and installation are not damaged.

I've tried three different ways and I keep getting "Error 13: Invalid or unsupported executable format".

```

title		 Microsoft Windows XP
root 		(hd3,0)
savedefault
makeactive
chainloader +1

```

```

title		 Microsoft Windows XP
map 		(hd0) (hd1)
map 		(hd1) (hd0)
root 		(hd3,0)
savedefault
makeactive
chainloader +1

```

```

title		 Microsoft Windows XP
map 		(hd0) (hd3)
map 		(hd3) (hd0)
root 		(hd3,0)
savedefault
makeactive
chainloader +1

```

---

### Post by FrozenFlame22 on 2008-03-06
*bump*

I've just spent the last couple of hours pouring over documentation that I really just don't understand.

---

### Post by jmstern on 2008-03-06
I have been through just about every flavor of Linux with Windows (2k) on the  same machine.  Windows has to be resident first - and they play well together if you use the Windows boot loader.  My trouble occurred when i put Ubuntu on new laptop with Vista, and let Ubuntu load the boot loader... so long Vista - which is what I wanted anyway.

---

### Post by adrian15 on 2008-03-07
> **FrozenFlame22 said:**
> *bump*

I've just spent the last couple of hours pouring over documentation that I really just don't understand.

Hi FrozenFlame,

When you boot Ubuntu (in the selection screen) press the letter 'c'.

grub prompt should appear. Something like:
```

grub>

```

Now write:
```

grub>cat (hd0,

```
and press the <TAB> key once or twice.

Then write:
```

grub>cat (hd1,

```
and press the <TAB> key once or twice.

Then write:
```

grub>cat (hd2,

```
and press the <TAB> key once or twice.

Then write:
```

grub>cat (hd3,

```
and press the <TAB> key once or twice.

Write the results of these <TAB>s into a paper, write them back here, and with that information I will be able to boot your Windows from Linux.

I bet that the right piece of code for you it is:

```

title Win
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
boot

```

Because from the BIOS point of view your Windows is on a second hard disk.

But I need to see that TABs results before being sure 100%.

adrian15

P.S.: The <TAB> trick is more effective than the fdisk -l output.

---

### Post by FrozenFlame22 on 2008-03-07
Thanks for replying Adrian15!

I followed your instructions using the tab trick, but now I'm getting worried that there's something else wrong. Either way, I'm sure you can make much more sense of it than I can.

Results of cat (hd0,
```
Possible partitions are:
     Partition num: 0, filesystem type is ext2fs, partition type 0x83
     Partition num: 4, filesystem type is unknown, partition type 0x82
```

For all of the others, it would complete the line to add "0)" but gave no other output. For example:
cat (hd1,
cat (hd1,0)

Twice the computer would hang after cat hd3,.

---

### Post by FrozenFlame22 on 2008-03-07
I just tried the code that you posted for your hunch and it worked! Thank you so very much for all of your help! =D> :KS :KS :KS :KS :KS

---

