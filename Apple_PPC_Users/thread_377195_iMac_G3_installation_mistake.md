---
title: "iMac G3 installation mistake?"
date: 2007-03-05
forum: Apple PPC Users
---

### Post by dagosta2010 on 2007-03-05
Hello
I accidentally installed the server install CD on my iMac G3, 600MHz and I just realized it.  So is there still a way to get a graphic user interface?  Should i try to install by using a Live CD for Ubuntu 6.10 and see if it will install?  What should I do??  Please help me!
Thanks

---

### Post by jazzman on 2007-03-05
Yes, you can get a UI. Here are a couple:

Gnome:

sudo apt-get install gnome

KDE

sudo apt-get install kde

Either of these commands at the command line should get you a UI

Then run either, for Gnome

sudo killall -HUP gdm

Or for KDE

sudo killall -HUP kdm

Good luck!

---

### Post by dagosta2010 on 2007-03-05
oh my gosh!! Thanks so much!  I got so scared there for a few days worrying about fixing it.  Thank you thank you thank you!!!

---

