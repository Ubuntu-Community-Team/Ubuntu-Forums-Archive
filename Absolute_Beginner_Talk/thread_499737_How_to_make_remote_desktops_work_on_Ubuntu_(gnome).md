---
title: "How to make remote desktops work on Ubuntu (gnome)?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by atri_2k7 on 2007-07-12
Hi,
I'm a newbie to the Ubuntu world and yesterday I was trying to use krdc (remote desktop utility for KDE) which is provided in the Synaptic Package Manager for Ubuntu 6.06. It didn't work - the connect button was not getting highlighted. 
Do I specifically need to install KDE to use this application or I can make it run from GNOME also? If so, how?

---

### Post by bodhi.zazen on 2007-07-12
> **atri_2k7 said:**
> Hi,
I'm a newbie to the Ubuntu world and yesterday I was trying to use krdc (remote desktop utility for KDE) which is provided in the Synaptic Package Manager for Ubuntu 6.06. It didn't work - the connect button was not getting highlighted. 
Do I specifically need to install KDE to use this application or I can make it run from GNOME also? If so, how?

I do not know krdc.

Try "Terminal Server Client" (it is in the gnome menu Applications -> Internet).

Works very well ;)

---

### Post by HermanAB on 2007-07-13
Yup, krdc doesn't work for me either, but I suspect it is because I haven't read the man page either.

However, rdesktop works perfectly OK:
$ rdesktop 192.168.1.2

The default port is 3389, if you have configured Expee to something else, then do something like this:
$ rdesktop 192.168.1.2:1234

Cheers,

Herman

---

### Post by atri_2k7 on 2007-07-13
Thanks for helping me out. The Terminal Server Client is working for me :)

---

