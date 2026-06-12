---
title: "grub, installing ubuntu in external drive (macbook), Problem"
date: 2020-09-02
forum: Apple Hardware Users
---

### Post by rnss on 2020-09-02
[CENTER]
[/CENTER]
Hollo everyone,
How is your life after getting a grub problem kkkkkk . 
My laptop is MacBook pro 2018 (i7 16gb ram)
 
**Here is my problem with details:**
I’m trying to install ubuntu 20.04.1 in external SSD (Samsung 5T).
I put 16gb for swap (logical, end of the space) and the rest for Ext4 journaling file system (mount point: /).
 
It started installing so good until this massage appeared
[ATTACH=CONFIG]286866[/ATTACH]

That’s when my computer start lagging so I restart it but a new disk appeared ( even the ssd and flash are un plugged) 
 [ATTACH=CONFIG]286867[/ATTACH]

This Text comes after I enter it:
[ATTACH=CONFIG]286868[/ATTACH]

I wrote exit …
I erased the disk and reinstall it again and I got the same problem.
This statement was in installing details:
[ATTACH=CONFIG]286869[/ATTACH]

But after pressing ok, it didn’t lag, instead I got this massage:
[ATTACH=CONFIG]286870[/ATTACH]
 
 
I was happy at this point.. hhhh :(

 till this happened
.
.
.

it follows in the next post

---

### Post by howefield on 2020-09-02
Thread moved to the "*Apple Hardware User*" forum.

---

### Post by rnss on 2020-09-02
this appeared immediately after restart:
[ATTACH=CONFIG]286874[/ATTACH]

 Exit

open ‘efi boot’ disk to check if it's really worked

[ATTACH=CONFIG]286875[/ATTACH]

Help please I've two subjects on this term depends on linux :(

---

### Post by oldfred on 2020-09-02
Do you have an ESP - efi system partition on external drive. 
Is external drive partitioned as gpt?

I do not know Mac, but PC systems boot from ESP and /EFI/Boot/bootx64.efi on external drives.
[https://askubuntu.com/questions/904135/modified-mac-bootloader-after-installing-ubuntu-on-external-hdd](https://askubuntu.com/questions/904135/modified-mac-bootloader-after-installing-ubuntu-on-external-hdd)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

Many with Mac use rEFInd.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

