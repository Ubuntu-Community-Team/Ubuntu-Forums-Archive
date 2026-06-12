---
title: "Ubuntu stopped seeing USB disk"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by muxecoid on 2007-02-17
Ubuntu previously worked OK with USB disks but just stopped now...  USB card-reader and cellphone in USB disk mode do not work properly under linux, but worked once. What diagnostic tools do I need to run? What is the problem? Can I mount manually?

---

### Post by duality on 2007-02-17
I dont know how to configure that, there probably is some setting for it in the control panel or something, usually you need to have an entry in /etc/fstab and should work automatically, but you can mount them manually with:

first try:
mount -a

if that doesn't work then try:
mkdir /mnt/usb
mount /dev/sda1 /mnt/usb

---

### Post by muxecoid on 2007-02-19
Looks like I disabled USB in my custom-compiled kernel. I will search for the solution in the kernel-compilation thread. Thank you.

---

