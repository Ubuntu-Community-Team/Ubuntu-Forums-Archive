---
title: "Strange things happened during installation og Nvidia"
date: 2012-07-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by johan_olsen on 2012-07-01
Hi
I run 12.04 on my Asus laptop, 64-bit. While trying to install the drivers for Nvidia grafic card (yes, I saw Linus Torvals yelling at Nvidia) everything froze and I had to take a hard restart. 

Then the login screen (Gnone panel) looked ok, but when I logged inn, the screen blinked and sent me back to the login screen. Some investigation showed this:

In the password file my user, xt, was absent. 
In the password file the machine name, milliways, looked like a user with my name. 
My home directory, /home/xt was gone, but now renamed /home/milliways. 

So, how can this happen? How can I log in from Gnome as milliways, when this user don't appear in the list of users? 

When I log in as guest, I am not allowed to su- to edit the password file. I would like to save my files before a reinstall. 

I hope I have explained clear here - will love some help.

Johan.

---

