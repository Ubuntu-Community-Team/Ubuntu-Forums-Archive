---
title: "Select CD-Rom Boot type on Mac-Mini 2.1"
date: 2017-09-25
forum: Apple Hardware Users
---

### Post by yan_solo on 2017-09-25
HI, I used to make dvd that would load just fine on mamy mac mini, but these day I want to install a 64 OS, ubuntu or xubuntu. It keep getting me the message after a black screen
[HTML]
Select CD-Rom Boot type  1 or 2.[/HTML]

If I press and hold 1 it will show 1 as selection, but will never start.

I tryed many versions and it still give me that message. Except on older version in 32 bits only. I even burned at 6x.

---

### Post by kevin160 on 2017-09-27
How old are your blank disks?  If you're like me, you have an old stack that has probably expired or your disk is a bit dusty.  You could try burning another disk to see if that helps.  I always just install via USB sticks. 

Googling around I can't tell if the 2,1 has a 32- or 64-bit EFI.  If 32-bit, go here:

[Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)]("https://ubuntuforums.org/showthread.php?t=2287767")

---

### Post by yan_solo on 2017-10-01
> **kevin160 said:**
> How old are your blank disks?  If you're like me, you have an old stack that has probably expired or your disk is a bit dusty.  You could try burning another disk to see if that helps.  I always just install via USB sticks. 

Googling around I can't tell if the 2,1 has a 32- or 64-bit EFI.  If 32-bit, go here:

[Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)]("https://ubuntuforums.org/showthread.php?t=2287767")

My blank dvd are new and blanc. Philips brand, DVD +R

Thanks for your help. It seem I found that my cpu is only 32 bits. I tought because I had 2gb ram, I could run a 64 bit. 

[https://everymac.com/mac-answers/snow-leopard-mac-os-x-faq/mac-os-x-snow-leopard-64-bit-macs-64-bit-efi-boot-in-64-bit-mode.html](https://everymac.com/mac-answers/snow-leopard-mac-os-x-faq/mac-os-x-snow-leopard-64-bit-macs-64-bit-efi-boot-in-64-bit-mode.html)

---

### Post by kevin160 on 2017-10-01
Ah, yeah, it sounds like you have the 32bit EFI with 64bit processor.  The link I provided should help you to install the 64bit version of Ubuntu.  If you are only have 2GB of ram you might be better off going with the 32 bit version of Ubuntu anyway, since it will use less RAM.

---

