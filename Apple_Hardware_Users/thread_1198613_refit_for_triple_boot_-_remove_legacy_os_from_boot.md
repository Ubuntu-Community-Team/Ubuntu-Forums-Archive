---
title: "refit for triple boot - remove legacy os from boot menu"
date: 2009-06-27
forum: Apple Hardware Users
---

### Post by drewjurecka on 2009-06-27
Hello,
I've successfuly installed a triple boot of OSX, WinXP and Ubuntu Jaunty on my Mac Pro (the OSX is on it's own HD in the first drive bay, and the XP and Ubuntu are on a drive in the last bay) 
When I boot up using rEFIt, I get all three options, and they all boot fine, but I also get 2 extra options to "boot legacy OS from HD" which both boot XP when I select them.  It's not a big deal, as I am able to use all three OSs I wanted to, but I'd love to get rid of those other two options in the boot menu since they are redundant.

Any ideas would be appreciated
thanks

- I've discovered that when removing the storage drive from bay 3, one of the legacy OS options disappears.  The other one appears to be coming from the HD in bay one that also has OSX on it.  Is it possible that there is something in the formatting of these drives that somehow looks like an operating system to rEFIt even though none exists?

---

### Post by Richardcavell on 2009-06-27
Hi.

Can you tell us what partitions you have on each of the drives?  And do any of those partitions have a /boot directory?

It seems to me that you might have a boot loader such as GRUB installed on some spare partitions.

Richard

---

### Post by drewjurecka on 2009-06-28
is there a terminal command I can use to output a comprehensive list of drive partitions?

---

### Post by drewjurecka on 2009-06-28
okay, here's what I found in gparted:

drive in bay 1: /dev/sda 596.17 GB (with OSX installed on it - this drive does seem to contain one of the legacy os rEFIt is picking up)
Partition: /dev/sda1
File System: fat32
Label: EFI
Size: 200mb
Used: 18.1mb
Flags: boot

Partition: /dev/sda2
File System: hfs+
Label: OSX
Size: 595.73gb
Used: 364.00gb

and there's 253.51 MB of unallocated space

The other drive that it seems to think there's a legacy os on is /dev/sdc (bay 3 - no OS installed on it.  It's just used as a storage drive)

Partition: /dev/sdc1
File System: fat32
Label: EFI
Size: 200mb
Used: 3.09mb
Flags: boot

Partition: /dev/sdc2
File System: hfs+
 Label: Storage
 Size: 931.19gb
 Used: 318.96gb

and there's 125.53 MB of unallocated space

is this enough info?

is the problem caused by the EFI partition?  if so, can I safely delete it from the storage drive without screwing up the drive?

Thanks!

---

### Post by drewjurecka on 2009-06-28
I can't seem to find a /boot folder on my OSX disk.

---

### Post by Richardcavell on 2009-06-28
Drewjurecka,

Can you go into OS X and get a Terminal and type "bless --info", and post the output here?

With the configuration that you've just listed, what exactly do you see on the rEFIt boot screen?  Do you have a drive in bay 2?  Where are XP and Ubuntu installed?

Richard

---

### Post by _mario_ on 2009-06-29
> **drewjurecka said:**
> 
..., but I also get 2 extra options to "boot legacy OS from HD" which both boot XP when I select them.  It's not a big deal, as I am able to use all three OSs I wanted to, but I'd love to get rid of those other two options in the boot menu since they are redundant.

Any ideas would be appreciated


looks like windows XP and/or linux installed boot code into the disks' MBR. this is not needed as long as all OSes have their boot code on their partition (recommended, and seems to work). so just clear the MBRs' boot codes by running:
```
dd if=/dev/zero of=/dev/sda bs=440 count=1
```
from within OSX or Ubuntu.

> **drewjurecka said:**
> 
is the problem caused by the EFI partition?  if so, can I safely delete it from the storage drive without screwing up the drive?


no. yes.

ciao,
Mario

---

### Post by drewjurecka on 2009-06-30
Here's the output of the "bless --info" terminal command:

finderinfo[0]:    149 => Blessed System Folder is /System/Library/CoreServices
finderinfo[1]: 549303 => Blessed System File is /System/Library/CoreServices/boot.efi
finderinfo[2]:      0 => Open-folder linked list empty
finderinfo[3]:      0 => No OS 9 + X blessed 9 folder
finderinfo[4]:      0 => Unused field unset
finderinfo[5]:    149 => OS X blessed folder is /System/Library/CoreServices
64-bit VSDB volume id:  0x347ADA2BF9D63B0A

I have 4 drives installed:
 have figured out which ones cause rEFIt to see Legacy OSs by starting up the computer with various drives removed until I figured out which ones made a difference:

*Drive in Bay 1: OSX, also causes one Legacy OS to appear on rEFIt menu
Drive in Bay 2: storage, seems to have no effect on rEFIt menu
*Drive in Bay 3: storage, seems to cause one Legacy OS to appear in rEFIt menu
Drive in Bay 4: 2 partitions, one contains Ubuntu Linux, the other XP

Thanks
Drew

---

### Post by drewjurecka on 2009-07-01
Hi Mario,
When I ran the script you sent me, I got the following message: "dd: /dev/sda: Operation not supported"

what was supposed to happen and how can I fix it?

thanks
Drew

---

### Post by drewjurecka on 2009-07-01
is there some way I can check to see if any unnecessary boot codes are installed?

---

### Post by _mario_ on 2009-07-03
> **drewjurecka said:**
> Hi Mario,
When I ran the script you sent me, I got the following message: "dd: /dev/sda: Operation not supported"
what was supposed to happen and how can I fix it?

you'll need to run it using sudo:
```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

> **drewjurecka said:**
> is there some way I can check to see if any unnecessary boot codes are installed?

the only way i know of is reading the boot code to a file:
```
sudo dd if=/dev/sda of=some-file bs=440 count=1
```

and using a hex editor to check whether the content is something other than completely zero.

ciao,
Mario

---

### Post by pxwpxw on 2009-07-03
```

 sudo hexdump -Cn512 /dev/sda

```
And dont dd anything to the disk before saving from the disk to a file to restore if it goes wrong.

---

### Post by drewjurecka on 2009-07-03
Mario, I fixed the issue using the dd command you sent me.  It wouldn't run from an OSX terminal, but worked from Linux.  
Thanks!

---

### Post by _mario_ on 2009-07-04
> **drewjurecka said:**
> Mario, I fixed the issue using the dd command you sent me.  It wouldn't run from an OSX terminal, but worked from Linux.  
Thanks!

no problem. for those that need to run this command from OSX, you'll have to substitute /dev/sda, /dev/sdb,... with /dev/disk0, /dev/disk1,...

ciao,
Mario

---

### Post by la_tristesse on 2010-01-19
So the terminal command would be:

> sudo dd if=/dev/zero of=/dev/disk0 bs=440 count=1


Because I'm only getting: 

> dd: /dev/disk0: Resource busy

Would appreciate help.

---

### Post by kyleriege on 2010-01-28
Im having the same issue. 
> dd: /dev/disk0: Resource busy

---

### Post by linuxopjemac on 2010-01-29
try it from within Linux in a live environment.

---

### Post by wersdaluv on 2011-01-02
After running **sudo dd if=/dev/zero of=/dev/sda bs=440 count=1**, I lost my Ubuntu entry instead of the Legacy OS. 

My setup is dual booting OS X and Ubuntu with a FAT32 partition for shared files.

---

### Post by wersdaluv on 2011-01-02
Looks like **sudo dd if=/dev/zero of=/dev/sda bs=440 count=1** nuked my Ubuntu partition. Reformatting now. 

My setup is 
/dev/sda1 - fat32 EFI
/dev/sda2 - hfs+ Macintosh HD
/dev/sda3 - fat32 shared media drive for OS X and Ubuntu (where rEFIt got "Legacy OS")
/dev/sda4 - ext4 Ubuntu root
/dev/sda5 - ext4 Ubuntu home
/dev/sda6 - linux-swap

What command do I run to remove the "Legacy OS" on my rEFIt?

---

