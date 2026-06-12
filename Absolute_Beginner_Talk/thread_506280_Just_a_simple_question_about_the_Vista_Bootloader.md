---
title: "Just a simple question about the Vista Bootloader"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Tuffy on 2007-07-21
I just have a simple question about how to set up the Vista boot loader to be able to boot into GRUB. The reason behind this is that I don't want to loose the restore option in the bootloader.

So, does anyone here know how to configure the Vista bootloader to boot into my Linux partition? Currently, I have 2 partitions, one with the recovery files and one with vista, adding up to 120 GBs of storage capacity. I'll just simply shrink the vista partition, leaving 50% for Vista, and 50% for linux.

Can't wait to finally do something on this computer. I thought Vista was bad, but not THIS bad :P

thanks

---

### Post by Steve1961 on 2007-07-21
> **Tuffy said:**
> I just have a simple question about how to set up the Vista boot loader to be able to boot into GRUB. The reason behind this is that I don't want to loose the restore option in the bootloader.

So, does anyone here know how to configure the Vista bootloader to boot into my Linux partition? Currently, I have 2 partitions, one with the recovery files and one with vista, adding up to 120 GBs of storage capacity. I'll just simply shrink the vista partition, leaving 50% for Vista, and 50% for linux.

Can't wait to finally do something on this computer. I thought Vista was bad, but not THIS bad :P

thanks

Hi there.  The easiest way to do this is to install easyBCD:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Once installed you can easily add any Linux partition to the vista bootloader

---

### Post by Tuffy on 2007-07-21
Thank you for the quick answer! This was just what I wanted :)

problem solved

---

