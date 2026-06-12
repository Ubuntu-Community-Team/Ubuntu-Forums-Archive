---
title: "eee 900 What is the latest advice?"
date: 2011-12-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by coldraven on 2011-12-16
Hi, I've been trying to help my friends who have just bought an eee 900.
I have Googled and sniffed about but I'm confused because a lot of the results are fairly old.
I don't have the machine with me at the moment so replies to this post may be slow.
The situation so far is that they already installed Ubuntu 10.04 desktop edition which is working. But they installed it to the 16GB disc leaving the 4GB disc untouched.
On boot-up grub shows about six options the default one being the 10.04 install.
I booted from the Live CD and tried to run gparted but it would crash on startup.
So can anyone please answer a few questions?
1. Does UNR still exist?
2. Should I just install 11.10?
3. Should I put / on the 4GBdrive  and /home on the 16GB drive?
4. What is the latest advice concerning ext2,3,or 4 file systems?
5. Should I create a swap partition or not?

All advice and links gratefully received. TIA

---

### Post by snowpine on 2011-12-16
1. No, starting with 11.04 there is no separate "netbook" edition because Unity is designed for netbook, laptop, desktop. Also don't forget Xubuntu, Lubuntu, etc... these are "lightweight" versions that run faster and take up less disk space. 
2. Up to you, try Live USB's of both and decide which you like better. :)
3. Completely up to you. I have heard that the 4gb drive is much faster than the 16gb on some of the EEE models. If that is the case for you then I recommend installing to the 4gb and using the 16gb for extra storage of documents/files.
4. ext4 is my vote
5. How much RAM do you have, and what % used under typical circumstances? If you routinely use a significant % of your RAM then you may benefit from swap.

---

### Post by coldraven on 2011-12-16
> **snowpine said:**
> 1. No, starting with 11.04 there is no separate "netbook" edition because Unity is designed for netbook, laptop, desktop. Also don't forget Xubuntu, Lubuntu, etc... these are "lightweight" versions that run faster and take up less disk space. 
2. Up to you, try Live USB's of both and decide which you like better. :)
3. Completely up to you. I have heard that the 4gb drive is much faster than the 16gb on some of the EEE models. If that is the case for you then I recommend installing to the 4gb and using the 16gb for extra storage of documents/files.
4. ext4 is my vote
5. How much RAM do you have, and what % used under typical circumstances? If you routinely use a significant % of your RAM then you may benefit from swap.

Thanks, downloading Xubuntu 11.10 right now.

---

