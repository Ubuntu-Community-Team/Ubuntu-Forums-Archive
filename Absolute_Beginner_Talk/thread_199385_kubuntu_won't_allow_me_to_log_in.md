---
title: "kubuntu won't allow me to log in"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-18
I get the logon screen type my password then i get a black screen then back to the login screen..I can log in thru console thou.. Any ideas where to start?

---

### Post by catlett on 2006-06-18
seems like your x session is messed up somehow. If you can get to a command line enter```
 sudo dpkg-reconfigure xserver-xorg
``` That will take you through the x server setup again i.e. detect your monitor,video card, keyboard, etc. Let it run and then reboot, hopefully the new reconfiguration you just made will work.

If not you may have to reinstall kde with```
 sudo aptitude kubuntu-desktop
``` Try to reconfidure x and see what happens.

---

### Post by lime4x4 on 2006-06-18
thanks i'll give it a try...The other day i took the new kernel update along with a bunch of other updates...Thanks

---

### Post by sheepscrossing on 2008-04-03
I have the same problem - Black screen after attempting to login and then back to the KDE login.  I tried running the "sudo dpkg-recofigure xserver-xorg" and took the defaults.  Now KDE won't start at all.  It just hangs on the black and white screen or asks me to login without the graphic screen....   Is it reload time?  BTW the aptitude  kubuntu-desktop won't run either.....  It gives me a screen with the command parameters as if I had entered something incorrectly.  This is Ubuntu 7.10.
Thanks,:confused:

---

