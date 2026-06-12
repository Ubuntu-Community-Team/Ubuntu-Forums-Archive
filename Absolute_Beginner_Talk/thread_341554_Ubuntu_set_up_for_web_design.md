---
title: "Ubuntu set up for web design"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by musicmadsimon on 2007-01-18
Hi I've just heard about Ubuntu and know nothing of Linux except the LAMP setup is popular and this is all set up in the server version.    I want to be able to eventually create active server pages using say Dreamweaver,  php and  mysql,  test them,  then have them hosted elsewhere.   

Have Intel 1kh pc with 3 win98 partitions on one drive (music composition, internet, other) and data on others.   Can I replace a win98 partition with a combination of Ubuntu server and desktop or is this mad?  How? Thinking desktop may be  more user friendly for a novice.  

Does this  sound a sensible set up for web design and test or have I lost the plot??


thanks,  Simon

---

### Post by riven0 on 2007-01-18
The only difference between a Ubuntu server and Ubuntu desktop, is that the server edition doesn't come standard with the desktop. Everything else is there, which means you'll be booted up to a terminal screen. However, you have the option of adding on a desktop later on. All you have to do is type:

**sudo apt-get install ubuntu-desktop** or **sudo apt-get install kubuntu-desktop**, etc.

If you're not comfortable with just using the terminal, just go with the desktop install and add on the server packages later. That's all there is to it.

I recommend learning the terminal, though. It's easy once you get the hang of it, and your server will run faster without the overhead of the desktop. :D

---

### Post by musicmadsimon on 2007-01-19
Marvellous.  Thanks a lot.

---

### Post by louieb on 2007-01-19
I don't believe Dreamweaver  is available for Linux.  However I have heard that it will run on Linux by using wine. What is an Intel 1kh PC?  If you have a Pentium 1 the Ubuntu server won't run at all and the desktop version will be  very slow.

---

### Post by davebgimp on 2007-01-19
Try out NVU. It's a WYSIWYG for Linux

You can find it in Synaptic or just:

**sudo apt-get install nvu**

---

### Post by davebgimp on 2007-01-19
Also, if this is just for local development, you might want ot give [Xampp]("http://www.apachefriends.org/en/xampp.html") a try. I use it a lot and love it. Very easy.

---

