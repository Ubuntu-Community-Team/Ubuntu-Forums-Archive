---
title: "How should I go about checking my hard disk?"
date: 2013-05-08
forum: Any Other OS
---

### Post by gregoryshock on 2013-05-08
I was trying to post this on the Zorin Forums and I kept getting this message.

**Forbidden**

 You don't have permission to access /forum/posting.php on this server.
 Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.



I have reason to believe that my hard drive maybe going bad.  I am new to Linux, so I haven't been running it on an internal hard drive.  Instead I've been installing it onto a external hard disk that I feel comfortable with reformatting/repartitioning/re installing, for as often as I need to, while I'm getting the hang of things.  I wanted Linux to install as if it is going to a regular drive.  To do this, I simply remove my internal hard drive (unplug it)  then I boot my computer using the Zorin live Disc.  Then I simply plug in my external usb drive and then run the install.  It gives me a really weird Input/output error.  But when I hit retry, it installs.  If there is a really an input/output error, then why does retry even work?  My theory is, there is still an error that Linux chooses to ignore and because of that Zorin becomes buggy and crashes.  It does crash on me from time to time, and there is no way to shut down without holding down the computer button.

[[IMG]http://i1089.photobucket.com/albums/i357/ADDMan1010/Zorin/00_zpsd4420fcf.jpg[/IMG]]("http://s1089.photobucket.com/user/ADDMan1010/media/Zorin/00_zpsd4420fcf.jpg.html")

[[IMG]http://i1089.photobucket.com/albums/i357/ADDMan1010/Zorin/01_zpsd5a6b5c0.jpg[/IMG]]("http://s1089.photobucket.com/user/ADDMan1010/media/Zorin/01_zpsd5a6b5c0.jpg.html")

[[IMG]http://i1089.photobucket.com/albums/i357/ADDMan1010/Zorin/02_zps972f0ab9.jpg[/IMG]]("http://s1089.photobucket.com/user/ADDMan1010/media/Zorin/02_zps972f0ab9.jpg.html")

[[IMG]http://i1089.photobucket.com/albums/i357/ADDMan1010/Zorin/BadBlocks_zpsfe90af32.jpg[/IMG]]("http://s1089.photobucket.com/user/ADDMan1010/media/Zorin/BadBlocks_zpsfe90af32.jpg.html")

How should I go about checking my hard disk?

---

### Post by mips on 2013-05-09
You can install** [gsmartcontrol]("http://gsmartcontrol.berlios.de/home/index.php/en/Home")** which should be in the repos and check the SMART status to see if the drive itself reports anything bad. You can also run diagnostic tests.

Alternatively you could do the same from the cli using the **smartctl **command.

---

