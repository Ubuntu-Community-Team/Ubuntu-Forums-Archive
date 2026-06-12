---
title: "Installation Help."
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-28
I am going to reinstall Ubuntu 5.10 cuz i only have a swap of 8 Mb and am going to increas it to 512 Mb.

So just wanted to know what the kernels mean during installation.

I get to choose the following kernels.

1. linux-386
2. linux-image-386
3. linux-image-2.6.12-10-386.

Which one is the best for me.

I have a 2.26 Ghz processor 
256 Mb of Ram
intel x86

---

### Post by Kilz on 2006-06-28
[QUOTE=hardfire_avk]I am going to reinstall Ubuntu 5.10 cuz i only have a swap of 8 Mb and am going to increas it to 512 Mb.

So just wanted to know what the kernels mean during installation.

I get to choose the following kernels.

1. linux-386
2. linux-image-386
3. linux-image-2.6.12-10-386.

Which one is the best for me.

I have a 2.26 Ghz processor 
256 Mb of Ram
intel x86[/QUOTE]
First off I would install 6.06 Dapper Drake insted of 5.10. Second I would let the installer chose a kernel to start out with. Then install and try others after you are up and running.

---

### Post by simone.brunozzi on 2006-06-28
Hi there hardfire_avk from Nepal!

It is not strictly necessary to reinstall just to modify the swap... you can use gparted to manually resize your current partition, as follows:

take one partition (call it A) that is near the swap partition (call it B);
free some 504 MB from A;
delete B;
create a new partition in the free space of 512 MB;
assign it to swap.

Using gparted it is very easy.

About the kernel: check for 686 versions instead of 386, you'll get a significant performance boost.

Cheers,


[QUOTE=hardfire_avk]I am going to reinstall Ubuntu 5.10 cuz i only have a swap of 8 Mb and am going to increas it to 512 Mb.

So just wanted to know what the kernels mean during installation.

I get to choose the following kernels.

1. linux-386
2. linux-image-386
3. linux-image-2.6.12-10-386.

Which one is the best for me.

I have a 2.26 Ghz processor 
256 Mb of Ram
intel x86[/QUOTE]

---

### Post by simone.brunozzi on 2006-06-28
Oops, Kilz beat me at the photofinish!

Anyway, if you want to keep 5.10, follow my instructions.
If you want to try 6.06 (which is way much better), you have to reinstall.
Be sure to properly partition your hard drive this time!

Cheers,

---

### Post by hardfire_avk on 2006-06-28
I have asked to ship the 6.06 CD's and will be here in some more weeks. However where can i get Gparted from?

And yeah.. I have a dual boot system.. ubuntu and Xp. So doing the partition from Gparted wil affect the Xp system or not.

---

### Post by simone.brunozzi on 2006-06-29
Gparted is in the default Ubuntu 6.06 disc, under system or administration (can't remember, now I'm under Kubuntu).

Gparted will resize an existing partition, usually it doesn't affect existing winXP partitions (with NTFS filesystem), however, if you have valuable data, I suggest you to backup them.

Cheers,

---

