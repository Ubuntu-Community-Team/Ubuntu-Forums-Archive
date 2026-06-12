---
title: "Please help with Macbook Pro installation"
date: 2015-03-02
forum: Apple Hardware Users
---

### Post by gareth12 on 2015-03-02
Hi guys, 

I have a Macbook Pro (Mid 2012) 2.3 Intel Core i7 with 8GB of RAM.

I'm aiming to dual boot Ubuntu with OS X and I'm nearly there.  The version of Ubuntu is 13.04 as it's compatible with my computer.  

I installed Ubuntu and I'm not getting the "missing operating system" error when I try to boot into it. 

I'm using rEFInd as my boot manager.  Here is my hard drive layout:

```
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                  Apple_HFS apple                   366.9 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   4:       Microsoft Basic Data                         132.2 GB   disk0s4
   5:                 Linux Swap                         133.2 MB   disk0s5

```

A few things I"m unsure of.  I don't know why disk0s4 is called Microsoft Basic Data.  

Also, I have messed up that swap partition, haven't I?  I honestly don't know what I was thinking when I only made it 133.2mb!!! 

Any help is appreciated.

---

### Post by este.el.paz on 2015-03-08
You should probably run the install again, but you should be able to use 14.04 of some type.  In terms of the "microsoft data" . . . that is obviously some kind of error/bug problem . . . .  In GParted can you see that data has been installed in the "microsoft" partition?  Technically you could boot the install disk and use GParted to enlarge your swap partition, but seems like something went wrong, like perhaps you didn't "format" that microsoft partition to "ext4"??? so it did a "default" format?  Also for me for the most part I've needed to set aside a 10 MB partition formatted as "bios_boot" so that the installer could find where to put GRUB, if I don't do that Manually, best in front of the "home"/root partition, GRUB doesn't seem to get installed and I can't boot the system, even with rEFInd installed . . . .

e.e.p.

---

