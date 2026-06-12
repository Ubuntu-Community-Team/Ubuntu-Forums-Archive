---
title: "Trying to install ubuntu"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by firehawk on 2008-01-02
Hi. Anyways, I'm new to the whole Linux OS system. Well, I downloaded Ubuntu 7.04 and booted it up and I got to the screen where it says install or start ubuntu and i installed it, well, it went through all the normal procedures till the screen just went completely white and then turned blank and did nothing. Well, eventually after hours of tinkering with the CD i finally booted the cd pressed f4 changed my vga settings and then clicked f6 for other options and booted where it says start or install linux with vga=771. Well, it did finally boot it all the way to where I'm now at. It loads the desktop and that's what I'm actually using to type to you now. So then I tried to install it to my hard drive (the full hard drive) and it installs and then the system reboots. When it starts to load Ubuntu from my hard drive it goes through a few screens and then turns completly white again. (this is without the live cd in) and it won't do anything... What's going on? What am I doing wrong? Thanks for all your help.

---

### Post by overdrank on 2008-01-02
> **firehawk said:**
> Hi. Anyways, I'm new to the whole Linux OS system. Well, I downloaded Ubuntu 7.04 and booted it up and I got to the screen where it says install or start ubuntu and i installed it, well, it went through all the normal procedures till the screen just went completely white and then turned blank and did nothing. Well, eventually after hours of tinkering with the CD i finally booted the cd pressed f4 changed my vga settings and then clicked f6 for other options and booted where it says start or install linux with vga=771. Well, it did finally boot it all the way to where I'm now at. It loads the desktop and that's what I'm actually using to type to you now. So then I tried to install it to my hard drive (the full hard drive) and it installs and then the system reboots. When it starts to load Ubuntu from my hard drive it goes through a few screens and then turns completly white again. (this is without the live cd in) and it won't do anything... What's going on? What am I doing wrong? Thanks for all your help.

HI and welcome, you may try the addition to the kernel as you did with the live cd,
You can and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add vga=771 ( as you did with the live cd) and then hit enter and then  b to boot. *What is the model of the graphics card on your system*?Hope this helps. Good luck!

---

### Post by cecure on 2008-01-02
Are you using Grub to boot your computer?

---

### Post by firehawk on 2008-01-03
NVIDIA GeForce Go 6150
AMD Turion 64X2 Mobile Technology
1024 MB of RAM

I tried the alternate download the text based installer for 7.10 and it installed on my hard drive. But, when I boot from hard drive it comes up to the splash screen and when it says it's loading it stops at almost half way and won't load anymore. I've let it set there for 2 hrs and it still sets there and doesn't load. Any ideas? Yes I am using Grub to boot my computer.

---

### Post by firehawk on 2008-01-04
I'm now a 100% percent ubuntu user!! :) All I did was like you said add vga=791 to the command line upon boot and then when i made it to the actual desktop, i installed the nvidia linux drivers and changed the screen resolution. Now, everything works properly.

---

