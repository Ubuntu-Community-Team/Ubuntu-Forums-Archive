---
title: "Triple Boot Suggestions"
date: 2008-11-29
forum: Apple Hardware Users
---

### Post by sauce345 on 2008-11-29
Hello, i just purchased a new Macbook Pro unibody (5,1) and i can't wait to get this thing set up and going.  I was wondering if anyone has any good articles or tips for doing this.  I found this article and am going to give it a try:

[http://blog.geeklimit.com/2008/07/02/triple-boot-macbook-pro-osx-leopard-vista-64-bit-and-ubuntu-804-64-bit/](http://blog.geeklimit.com/2008/07/02/triple-boot-macbook-pro-osx-leopard-vista-64-bit-and-ubuntu-804-64-bit/)

Can't wait to get ubuntu up and going on this.  Has anybody been having any big problems with the new mackbooks and ubuntu?:)

---

### Post by spencercarran on 2008-11-29
The procedure I used was somewhat different from that one. I used Bootcamp for Windows (giving Windows 1/3 of the hard drive) and then gave Ubuntu space from the OSX partition so that each OS had 1/3 of the hard drive space. Be sure to install the grub to the Ubuntu partition rather than the MBR to avoid breaking it. If you do break it, just stick in the Windows install disk and boot into recovery mode, it'll clean up whatever mess you make. I messed that up when I first started, but it wasn't a big deal since it can be fixed pretty easily after-the-fact. I used the instructions found at [http://blog.gnist.org/article.php?story=Triple-Boot-OSX-Ubuntu-Vista]("http://blog.gnist.org/article.php?story=Triple-Boot-OSX-Ubuntu-Vista") sans the swap file.

A word of advice though: use XP, not Vista, in your triple-boot. I made that mistake, and it's harder to fix than a broken MBR.

---

