---
title: "Have an old laptop, which completely ignores all Live CD's"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by itzme on 2006-12-30
I have an old Laptop which I would like to pass onto my 7yo daughter.  It is old, but it still works perfectly.  It has Windows 2000 installed on it.  Over the passage of time Windows has just become buggy and so many application do not work anymore.   I do not want to invest in an ebay copy of Windows 98 or 2000, so I want to put Linux on the Laptop.  

The laptop I have is a Toshiba Tecra 780cdm.  It has an external floppy and a cd drive.  As far as I can tell it has to basic requirements to run Linux.  What happens, I make a CD copy of the Live disk on my desktop,  when I put that disk in my laptop and power up,  it spins as if it will start installation and then nothing happens, my same old buggy Windows boots up.  

Am I doing something wrong to install the system?  There does not seem to be a simple walk though to refer to on this site.

Thank you for all replies.

PS, this laptop was made is the USA, tell you how far things have changed.

---

### Post by boopyg on 2006-12-30
You have to go to the BIOS and change the order of the things it looks to boot from.  Make sure that your CD drive is before your hard drive

---

### Post by Sef on 2006-12-30
Also have you burned the image as an iso file?

---

### Post by bakegoodz on 2006-12-30
First it could have trouble with burned media, older cdrom drives sometimes can't read the disk at all. Try burning at 8x or try a slow speed cd-rw. Second locate pressed cd somewhere (Ask someone at a LUG or buy one from Amazon), Ubuntu will send them free but it takes weeks to arrive. Also you can try Smart Boot Manager. It will boot off a floppy then it will boot whatever device you have. [http://btmgr.sourceforge.net/download.html](http://btmgr.sourceforge.net/download.html) Last, I've seen systems that have a external drive that will not boot any cd's. In this case try setting up a network boot install  or a PXE server, not the easiest thing to do if your a beginner, but there is a step by step walk through [http://www.howtoforge.net/ubuntu_pxe_install_server](http://www.howtoforge.net/ubuntu_pxe_install_server)

---

