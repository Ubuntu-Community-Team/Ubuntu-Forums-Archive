---
title: "Ubuntu Installation on iMAC G3"
date: 2009-10-11
forum: Apple Hardware Users
---

### Post by JonathanFB on 2009-10-11
I hope someone can help with this installation problem. I am try to install Ubuntu on an iMAC G3
I have downloaded the PowerPC version and burned a CD. I have been able to load the OS from the CD, so far so good. I have opened the xorg.conf file to edit the HorizSync 
and VertRefresh settings. After saving this file I am unable to load the GUI. I am only able to view the command line.
Any help will be appeciated.

Jonathan

---

### Post by rjcalifornia on 2009-10-11
hello there! 

in the command line login:

login with your username and password, then open the xorg.conf file with nano:

/* sudo nano etc/X11/xorg.conf */

compare with the xorg files that are around here, fix any errors, then save any changes, close it, and then type this:

/* sudo ybin -v */

restart and you'll have your gui again.

---

