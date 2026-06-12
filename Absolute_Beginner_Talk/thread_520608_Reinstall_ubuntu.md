---
title: "Reinstall ubuntu?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Jeppe1 on 2007-08-08
Yeah, I did some bad things to the x-serv and now I want to reinstall ubuntu or just heal the x-server... But how please? :(

---

### Post by silent1643 on 2007-08-08
depends on what you did?? you can fix things without being in xwindows

if the install process was smooth before and your not loosing a whole crap load of personal stuff i would say go ahead.

---

### Post by bluemarvel on 2007-08-08
> **Jeppe1 said:**
> Yeah, I did some bad things to the x-serv and now I want to reinstall ubuntu or just heal the x-server... But how please? :(

If you want to reinstall Ubuntu, just load your CD back into your CD-ROM drive and boot off of it. You should be prompted to install.  If it goes through the Live CD routine, you can install from there instead.

Just make sure you don't do what you did before to break X. :)

What's up with X anyway - is it something with the config? You might want to mess around with that before reinstalling from scratch.

Best of luck!

---

### Post by Jeppe1 on 2007-08-08
I tryied to get xgl to work with my damn ati videocard...
I will try using the cd:)
Thanks anyway

---

### Post by be4truth on 2007-08-08
2 things you can learn here: 

Always make a backup of the original configuration file before messing around. Ask how next time you mess ....

2nd thing - Linux systems can be repaired. The "reinstall" model is rather a windows user habit. Get rid of this habit in the first year Ubuntu. I reinstalled my last Linux 2 years ago because I couldn't fix it. The more you fix, the more you learn. At one point you can help others to fix their problem. It's really fun and the reward of community.
:)

---

### Post by silent1643 on 2007-08-08
> **Jeppe1 said:**
> I tryied to get xgl to work with my damn ati videocard...
I will try using the cd:)
Thanks anyway

did you edit your xorg.conf - and thats what broke x?

---

### Post by ajgreeny on 2007-08-08
Try sudo dpkg-reconfigure xserver-xorg in a terminal and go through the questions it asks by selecting tyhe defaults until you get to the video/graphics part.  There chose ati.  Good luck

---

