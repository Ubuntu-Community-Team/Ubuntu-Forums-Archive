---
title: "need boot/partition help"
date: 2009-06-30
forum: Apple Hardware Users
---

### Post by babybatter23 on 2009-06-30
so i have a macbook aluminum and have been dual booting ubuntu 9.04 32 bit on it and loving it however because of gaming and quicken purposes i would like to be able to boot XP in addition-- so using gpart i made a 5gb ntfs partition to boot windows from however when i boot my windows cd it says that i have reached the maximum number of partitions or something

right now my partitions are like this
dev/sda1 fat 32 -- boot 200mb using 18
dev/sda2- hfs+ macintosh HD 
dev/sda3 ext 3 linux
dev/sda7 linux swap which is also booted right now in addition 2 sda3
dev/sda6 this is the ntfs partition i made
dev/sda5 linux-swap
dev/sda4 linux swap

so my question is can i delete one of those linux swaps or somehow adjust the maximum number of possible partitions- thanks in advance

---

### Post by paul_be on 2009-06-30
the problem you are having is you need to install windows on a primary partition. these are sda1, sda2, and sda3  plus you may want more than 5gb to install windows, and a windows install will muck up grub.  You may want to try running windows in a virtual machine or just put it on another box:)

---

### Post by babybatter23 on 2009-06-30
how can i make a new sda3 partition ?

---

### Post by Richardcavell on 2009-06-30
Baby batter,

You want your Windows installation on sda4. Your Linux swap can be on sda5. (By the way, make sure you change this in fstab before you install Windows, otherwise your Linux might be tempted to write over your Windows installation with swapfile). 

As Paul suggested, 5 Gigs is pretty anaemic for Windows XP. Delete any unused partitions.

Richard

---

