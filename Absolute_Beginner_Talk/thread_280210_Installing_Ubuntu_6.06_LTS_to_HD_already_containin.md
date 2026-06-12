---
title: "Installing Ubuntu 6.06 LTS to HD already containing Windows XP"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Vijay Kumar on 2006-10-19
Hello,

I have recently received Ubuntu 6.06 LTS and wish to install it to my PC(2.80 GHzs,Pentium 4, 512 MB RAM)having only one Hard Disk of 40 GB and that containing Windows XP Professional installed in C:\ drive.Whole Hard Disk is partitioned in three partitions C, D & F of sizes ~ 15, 12 & 12 GBs respectivey, all in NTFS formats & F:\ is completely free.

Is there any way to install Ubuntu 6.06 LTS to F:\ and then having Windows XP Pro & Ubuntu as dual Operating Systems with default first choice of XP?

Thanking for reading it,

Vijay Kumar.

---

### Post by mercurysquad on 2006-10-19
Of course, when you are installing, just select your 12 GB partition which is totally free. I would guess it's called /dev/hda3 or /dev/sda3  (note the 3).

During the installation you will get the disk partitioner. Select Manual partition. What you have to do is to erase that partition. Then create a new extended partition in the empty space. And now create two new partitions inside the extended partition - one should be 530 MB, type "linux-swap" and the other should fill the remaining space, type "ext3".

Dual booting is automatically set up by Ubuntu, except that Ubuntu will be the default so if you dont choose XP while booting up, Ubuntu will start after 10 sec.

And trust me, if you set your default to XP, you will be using Ubuntu less and less and after a while you will just remove it (I did that!). So my advice is, stick to Ubuntu for at least a month, don't use XP at all. And then decide whether you want to keep it or not.

---

### Post by raul_ on 2006-10-19
Or you could create two partition from F: with a partition program that u are comfortable with and then just run the installation, and u shouldn't have any problem. Just install your root and swap partitions, in the ones u just created, and off u go :)

---

