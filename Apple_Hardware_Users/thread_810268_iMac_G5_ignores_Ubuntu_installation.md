---
title: "iMac G5 ignores Ubuntu installation"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by garbageguts on 2008-05-28
Hi forum,

After much google searching I managed to install Hardy Heron alongside Tiger on my iMac G5 (PPC). Here's what I did:

1) I disabled HFS+ Journalling using OnyX from within the Mac OS (Tiger 10.4.11).
2) I loaded up the Heron live CD using "live video=ofonly" at the yaboot prompt.
3) From there I used Partition Manager (Gparted) to resize my Mac OS partition from ~400GB to ~300GB (leaving ~100GB of free space for ubuntu (this took ~4 hours!)
4) asked Heron to install on the largest free space available.

All went well, but after restarting there was no yaboot prompt, it just loads Mac OS by default. It won't let me use Ubuntu! :(

I feel a bit useless getting so far and then falling at the last hurdle, but what can I do to get a yaboot options menu?

From Tiger I can see an extra HFS partition called "bootstrap" with files named "ofboot.b", "yaboot" and "yaboot.conf". I've attached them here.

Any help is appreciated.

---

### Post by pxwpxw on 2008-05-28
garbageguts

Your boot partition is /dev/sda2, and the installer should have reset the iMac boot-device to that, but maybe not. Boot files look ok.

Check from Tiger  terminal  using
```

$ nvram boot-device 
$ sudo pdisk -l

```

If thats the prob, it can be reset from tiger
```

$ man nvram

```

If not , something wrong with the yaboot install.

---

### Post by garbageguts on 2008-05-29
Thanks for your suggestions pxwpxw, but I think I need a little more help.

typing "nvram boot-device" gives me

```
boot-device     first-boot/@0:3,\\:tbxi
```

I have no idea what that means...

and typing "sudo pdisk -l" (that's a lowercase L, not a 1 as I thought a moment ago) gives me

```
Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:           Apple_HFS untitled                  1954 @ 576621045
 3:           Apple_HFS Apple_HFS_Untitled_1 576364005 @ 257040    (274.8G)
 4:     Apple_Bootstrap untitled             196382813 @ 576622999 ( 93.6G)
 5:     Apple_UNIX_SVR2 swap                   8416956 @ 773005812 (  4.0G)
 6:          Apple_Free Extra                   256976 @ 64        (125.5M)

Device block size=512, Number of Blocks=781422768 (372.6G)
DeviceType=0x0, DeviceId=0x0
```

By what you've told me am I correct in thinking I should type "nvram boot-device [number]" to get it to reset the boot partition, if so which [number] is correct? (I don't want to stuff things royally so I'm making sure here first!) I'm guessing [2]?

EDIT: no wait (after reading the man page for nvram and using the example) could it be

```
nvram boot-args="-s rd=*hd:2"
```?

Thanks again, this is a learning experience!

---

### Post by pxwpxw on 2008-05-29
Something went wrong,

1. the boot-device shoud have been set to  first-boot/@0:2,\\:tbxi 

and 

 2. the yaboot Apple_Bootstrap boot partition with the yaboot boot files should be the #2 1954 blocks,   - check the size of the partition where you got the yaboot files in your attachment.

and the installer should have set #2 to type "Apple_Bootstrap" NewWorld  Boot_Block and "blessed" it. - not partition #4 93.6G

3, All this should be automatic for the installer, and not require any user input other than selecting to install in largest free space.

4. Need to clarify before  further action.

(note - you set boot-device like this, but not just now )
  $ sudo nvram boot-device="first-boot/@0:3,\\:tbxi"

---

### Post by Jammy4041 on 2008-05-29
Try Pressing the Option Key on startup- Does that give you two Hard Drive Icons (one with Tux the Penguin and the Other with a X in it?)

From there on, I think you can then boot Ubuntu
Just thinking, that's all.

---

### Post by garbageguts on 2008-05-29
@pxwpxw: I am sorry, I failed to mention that before I came here for help I messed around with Gparted on the live CD and swapped the "boot flags" between partition #2 and #4 in a naive attempt to fix things myself. I have now reversed that. #2 is the bootstrap now.

But the problem still persists; 

```
boot-device     first-boot/@0:3,\\:tbxi
```

```
Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:     Apple_Bootstrap untitled                  1954 @ 576621045
 3:           Apple_HFS Apple_HFS_Untitled_1 576364005 @ 257040    (274.8G)
 4:     Apple_UNIX_SVR2 untitled             196382813 @ 576622999 ( 93.6G)
 5:     Apple_UNIX_SVR2 swap                   8416956 @ 773005812 (  4.0G)
 6:          Apple_Free Extra                   256976 @ 64        (125.5M)

Device block size=512, Number of Blocks=781422768 (372.6G)
DeviceType=0x0, DeviceId=0x0
```

Only now I can't see the bootstrap partition from Tiger, it appears to be hidden (Disk Utility can't see it either). Maybe it just needs to be "blessed"? (how do I do that?) or just "sudo nvram boot-device="first-boot/@0:2,\\:tbxi"?

@ Jammy4041: Thank you for your suggestion but holding the option key doesn't do anything, it just loads Tiger.

---

### Post by pxwpxw on 2008-05-29
**garbageguts**

Hang on a moment -

Dont try to fix it like that, the problem is that you messed with boot flags and the installer needs the partitioning types and flags to be correct before it can install the bootblock correctly.

 It should set these corectly  during the installer automatic partitioning. (Unless there is a bug in Hardy).

The simplest fix is to re-install. This time, first delete the 3 ubuntu partitions back to just the 1 free space you started with, and then let it install to the free space as before,  but do not fiddle with boot flags or partition types. You got that wrong.

At some late stage in the installer automatic partitioning you should be able to check that it has made a NewWorld  bootblock about 900KB, a root partition, and a swap partition. Do not change any flags or types, that was the problem.

---

### Post by garbageguts on 2008-05-30
Well, the problem with yaboot not loading was there before I messed with the boot flags, but never mind, I did as you suggested: deleted the 3 Ubuntu partitions using Gparted and let Hardy reinstall itself from scratch, aaand... It now works! I have Tiger and Hardy running side by side!

The only thing I did differently now was wait a *long* time for the Heron live CD to restart the computer after installing. The first time I installed I figured it had hanged (black screen, full fan noise after hitting the restart button) and powered it off myself - but maybe it was busy and the install got stuffed in some way by me forcing a shutdown...

Either way, thanks a lot pxwpxw; you have been very patient with me ;)

And incase you're wondering: heres the info from the Terminal (done from Tiger because I don't have internet through Hardy yet)

"nvram boot-device":
```
boot-device     /ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi
```

"sudo pdisk -l":
```
pdisk: No valid block 1 on '/dev/rdisk1'

Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:     Apple_Bootstrap untitled                  1954 @ 576621045
 3:           Apple_HFS Apple_HFS_Untitled_1 576364005 @ 257040    (274.8G)
 4:     Apple_UNIX_SVR2 untitled             196382813 @ 576622999 ( 93.6G)
 5:     Apple_UNIX_SVR2 swap                   8416956 @ 773005812 (  4.0G)
 6:          Apple_Free Extra                   256976 @ 64        (125.5M)

Device block size=512, Number of Blocks=781422768 (372.6G)
DeviceType=0x0, DeviceId=0x0
```

---

### Post by pxwpxw on 2008-05-30
> **garbageguts said:**
> Well, the problem with yaboot not loading was there before I messed with the boot flags, but never mind, I did as you suggested: deleted the 3 Ubuntu partitions using Gparted and let Hardy reinstall itself from scratch, aaand... It now works! I have Tiger and Hardy running side by side!

The only thing I did differently now was wait a *long* time for the Heron live CD to restart the computer after installing. The first time I installed I figured it had hanged (black screen, full fan noise after hitting the restart button) and powered it off myself - but maybe it was busy and the install got stuffed in some way by me forcing a shutdown...

Either way, thanks a lot pxwpxw; you have been very patient with me ;)

And incase you're wondering: heres the info from the Terminal (done from Tiger because I don't have internet through Hardy yet)

"nvram boot-device":
```
boot-device     /ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi
```

"sudo pdisk -l":
```
pdisk: No valid block 1 on '/dev/rdisk1'

Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:     Apple_Bootstrap untitled                  1954 @ 576621045
 3:           Apple_HFS Apple_HFS_Untitled_1 576364005 @ 257040    (274.8G)
 4:     Apple_UNIX_SVR2 untitled             196382813 @ 576622999 ( 93.6G)
 5:     Apple_UNIX_SVR2 swap                   8416956 @ 773005812 (  4.0G)
 6:          Apple_Free Extra                   256976 @ 64        (125.5M)

Device block size=512, Number of Blocks=781422768 (372.6G)
DeviceType=0x0, DeviceId=0x0
```
Good result, and thanks for reporting the details.

For your info, the Apple PPC Open Firmware uses aliases for the full pathnames,

 so

first-boot/@0

 is one alias for
 
/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0

other aliases sometimes used are hd or sd0 for the first hard disk.

some of this stuff is explained in ubuntu  Linux manual
 man yaboot yaboot.conf bootstrap ybin ofboot  yabootconfig

---

### Post by oswaldkelso on 2008-05-30
> **pxwpxw said:**
> Good result, and thanks for reporting the details.

For your info, the Apple PPC Open Firmware uses aliases for the full pathnames,

 so

first-boot/@0

 is one alias for
 
/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0

other aliases sometimes used are hd or sd0 for the first hard disk.

some of this stuff is explained in ubuntu  Linux manual
 man yaboot yaboot.conf bootstrap ybin ofboot  yabootconfig

I remember reading something about this but you put it much more succinctly. If I put the true path in for my scsi card it's recognized  if I put the alias I get a usb error! So to dual boot osx via my OF unsupported scsi card I must put the full path or it wont boot via the yaboot menu.

Interestingly Debian and Ubuntu failed to find the ofpath to the scsi but fedora and Yellowdog did?

---

