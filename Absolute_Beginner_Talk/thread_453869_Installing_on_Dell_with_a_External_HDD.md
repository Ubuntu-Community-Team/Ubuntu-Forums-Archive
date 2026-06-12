---
title: "Installing on Dell with a External HDD"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by themacupdate on 2007-05-24
So I am totally new to this Linux OS. I just wanted to make sure that it would be possible to install Ubuntu onto a external HDD. I have a computer with Vista (a Dell E521 AMD Dual Core AthlonX2 with 256MB graphics card and 2GB of ram.

The External Hard drive is a Segate 160GB HDD. I just want to make sure that it will be easy and painless.

---

### Post by k33bz on 2007-05-24
you shoudl be able to easily and painlessly install it on the external hdd, just amke sure you know which hdd it is you are installing to

---

### Post by themacupdate on 2007-05-24
Of course, I heard you can actually install Ubuntu via windows (really freaking cool) how to I make sure I have the dual boot option though is there an easy way to do this? I saw some stuff that showed all this command line stuff to get it to work and honestly I don't know command line and would probably screw something up.

---

### Post by confused57 on 2007-05-24
> **themacupdate said:**
> So I am totally new to this Linux OS. I just wanted to make sure that it would be possible to install Ubuntu onto a external HDD. I have a computer with Vista (a Dell E521 AMD Dual Core AthlonX2 with 256MB graphics card and 2GB of ram.

The External Hard drive is a Segate 160GB HDD. I just want to make sure that it will be easy and painless.

Make sure that you don't install grub to your internal hard drive mbr...if you do, you won't be able to boot your computer without the external drive connected.  If you Dell bios is capable of booting first to your USB external hard drive you should be able to install grub to the external hd mbr & select to boot first to it.  What you might want to do before you boot up the live cd to install Ubuntu is to set your USB drive to be the first hard drive booted in bios.  

If you can't boot first to USB, you could probably use the Super Grub Disk to boot your external drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

