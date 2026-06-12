---
title: "where are kernels located?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-11-07
I was just curious where the kernels are located in my file system. I ask this because I also have Suse installed on the same system and it won't automatically recognize kernel updates from Ubuntu.

---

### Post by bodhi.zazen on 2006-11-07
/boot

Your suse kernel is in /suse_root/boot

suse kernel is not the same as ubuntu kernel

---

### Post by mongooseman1128 on 2006-11-08
yeah I know that thing about suse kernel being differeny than my ubuntu kernel. it's just that I need to know where it's located so I can point grub to it

---

### Post by bodhi.zazen on 2006-11-08
> **mongooseman1128 said:**
> yeah I know that thing about suse kernel being differeny than my ubuntu kernel. it's just that I need to know where it's located so I can point grub to it

> root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/sda5 ro

root = suse or ubuntu root partiton in grub speak

kernel /boot/<kernel_image> root=suse/ubuntu_partition_linux_speak ro

HTH 8)

---

