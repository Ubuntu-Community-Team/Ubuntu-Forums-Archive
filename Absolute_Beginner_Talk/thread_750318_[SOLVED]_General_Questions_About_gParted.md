---
title: "[SOLVED] General Questions About gParted"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by FAMUgolfer on 2008-04-09
Thank you all for taking the time to help us noobs.

Originally when my friend installed 7.04 on my Acer Aspire 9300 laptop, he partitioned it so that I could dual boot XP with 30GB and Ubuntu with 90GB.  When I updated to gutsy via update-manager somehow my dual boot was lost along with those 30GB of space.  When I received my gutsy CD I decided to wipe out everything and start from scratch.

I also installed gParted b/c it seemed so convenient to know how much memory i have left.

My laptop claims to have a 120GB harddrive, but gParted says otherwise:
dev/hda1 ext3 109.27GB
dev//hda2 extended 2,52GB
dev/hda5 linux-swap 2.52GB
In the top right hand corner: dev/hda 111.79GB

Where did the rest of my 8.21GB (120-111.79) of space go?
Also where is hda3 and hda4?

Thank you for your responses and remember I'm a noob so please talk to me as if I'm an idiot.

---

### Post by aeiah on 2008-04-09
some gets taken off when rounding up numbers but most gets taken up by hard drive makers lying to you.

they measure megabyte as 1000 kb, whereas normal people measure it as 1024kbyte. this accounts for a few extra gigs on that size hdd

---

### Post by SlappyPappy on 2008-04-09
Your hard drive is all there it's just that the manufacturers use a different number. Here's the math so you can see what happens.


"40 GB" hard drive = 40,000,000,000 bytes / 2^30 bytes in a gigabyte = 37.25 GB

"50 GB" hard drive = 50,000,000,000 bytes / 2^30 bytes in a gigabyte = 46.57 GB

"60 GB" hard drive = 60,000,000,000 bytes / 2^30 bytes in a gigabyte = 55.88 GB

"80 GB" hard drive = 80,000,000,000 bytes / 2^30 bytes in a gigabyte = 74.51 GB

"120 GB" hard drive = 120,000,000,000 bytes / 2^30 bytes in a gigabyte = 111.76 GB

"150 GB" hard drive = 150,000,000,000 bytes / 2^30 bytes in a gigabyte = 139.70 GB

"160 GB" hard drive = 160,000,000,000 bytes / 2^30 bytes in a gigabyte = 149.01 GB

"200 GB" hard drive = 200,000,000,000 bytes / 2^30 bytes in a gigabyte = 186.26 GB

"250 GB" hard drive = 250,000,000,000 bytes / 2^30 bytes in a gigabyte = 232.83 GB

"300 GB" hard drive = 300,000,000,000 bytes / 2^30 bytes in a gigabyte = 279.40 GB

"320 GB" hard drive = 320,000,000,000 bytes / 2^30 bytes in a gigabyte = 298.02 GB

"400 GB" hard drive = 400,000,000,000 bytes / 2^30 bytes in a gigabyte = 372.53 GB

"500 GB" hard drive = 500,000,000,000 bytes / 2^30 bytes in a gigabyte = 465.66 GB

"750 GB" hard drive = 750,000,000,000 bytes / 2^30 bytes in a gigabyte = 698.49 GB

"1 TB" hard drive = 1,000,000,000,000 bytes / 2^30 bytes in a gigabyte = 931.32 GB

---

