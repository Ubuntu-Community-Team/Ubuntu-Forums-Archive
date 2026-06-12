---
title: "First Time Installation"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by thebooks on 2008-02-27
Hi  All, I am completely new to Linux, let along Ubuntu. So, I downloaded Ubuntu 6.06 Server Edition and did the following. Host system is an Intel Mac 2.2GHz Intel Core 2 Duo cpu, 2GB RAM, SATA hard drive. I am running Parallels Desktop and was hoping to install/test/learn Ubuntu Linux as a parallel machine. So, I went through the Parallels setup and then booted the guest os from the ubuntu 6.06 iso image. I went through the "install to hard disk" wizard and everything seemed to complete without any errors. But, when I try to boot the guest os, I get the following:
root (hd0,4)
  Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz-2.6.15-51-server root=/dev/mapper/Ubuntu-root ro quiet splash
      [Linux-bzImage, setup=0x1c00, size0x16d6e8]
initrd /initrd.img-2.6.15-51-server
      [Linux-initrd @ 0x1f941000, 0x6ae5f1 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.

Then nothing happens. Does anyone have any advice for this newbie to Linux? Thanks,

Tony

---

### Post by jan quark on 2008-02-27
do you really want to install the server edition?

for desktop use try the live CD or desktop edtion
also try to use the newset vrsion of ubuntu
7.10 gutsy gibbon

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by 3rdalbum on 2008-02-27
I think Parallels Desktop has some bugs in it which prevent Ubuntu from working on the Macintosh host OS. Highly ironic since Canonical and Parallels are "partners".

You should probably try some other virtualisation solution, or another distribution, until Parallels fixes the bug.

---

