---
title: "Ubuntu 10.11 on Asus G60J Install"
date: 2012-03-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Sokk on 2012-03-12
Greetings. I am currently trying to install Ubuntu Linux 11.10 on my Asus G60J from a USB, but I've encountered a problem. Since this is the first time I'm trying to install Ubuntu Linux, I'm afraid im going to need some help.

I am able to get into the Ubuntu Installer Boot Menu, I've tried selecting both "Run Ubuntu from this disk" and "Install Ubuntu on a Harddisk", but when the first purple "loading screen" has finished after clicking one of those options, my screen is covered with pixel garbage, with a black and white background.

I have found that this pixel garbage appears because my graphics card doesnt switch to the frambuffer mode properly. Help.Ubuntu.Com advices you to use the boot parameter fb=false video=vga16:off to disable the framebuffer console, but now I cant manage to write that command into the boot parameter, as I cant find out how to write the equal (=) sign. Usually on my keyboard the combination for writing = would be shift+0, but thats apperently not the command in Ubuntu Linux. Therefor I was wondering if anyone could tell me how to write that command, and if there is any other solution to my problem? 

Thanks.

---

### Post by 2F4U on 2012-03-12
If would suggest you try the nomodeset boot option. If you are in the Ubuntu grub menu, press F6 and select nomodeset. If this doesn't help, post you hardware specs.

---

### Post by Sokk on 2012-03-12
I didnt manage to figure out how to select nomedoeset, couldnt find anything about it on F6 either. :s.

---

