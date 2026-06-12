---
title: "choosing OS on startup"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by catz on 2006-07-30
I want to install on a PC but my wife needs windows. Is there some way to choose between them on startup? I can't find an answer in the documentation that seems to really apply.

---

### Post by taurus on 2006-07-30
Yes, you can choose which OS to start up with either GRUB or LILO.  Make sure you install GRUB (that's what most people use) on MBR when you get to that option during the installing process.

---

### Post by Touch.Code on 2006-07-30
Its Dual Booting. You need to partiton yur drive first!

---

### Post by duff on 2006-07-30
Isn't there a little message that says something along the lines of "Press ESC to see menu..." when you first boot your computer?

---

### Post by Touch.Code on 2006-07-30
It will startup and aks you to select your partiton. Then it just carries on from the boot screen with your selected choice!

Yes. There is a screen

---

### Post by meney on 2006-07-30
Your best bet is to install windows first. After you have windows working (to the extent that anybody can get windows to work ;P ), you can either use Partition magic in windows or the partition editor in the ubuntu install. See this guide for more detailed info ;)

[http://www.psychocats.net/ubuntu/installing.html]("http://www.psychocats.net/ubuntu/installing.html")

---

### Post by catlett on 2006-07-30
The Ubuntu installation will install the GRUB booloader and that will alow you to choose between Ubuntu and windows when your computer starts up.
Grub wil look something like this when you start up.
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/grub.jpg[/IMG]

Aysiu has a great site with lots of guides on ubuntu. [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
This one is specifically about the Live Install CD [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

