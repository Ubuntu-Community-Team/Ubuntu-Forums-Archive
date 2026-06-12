---
title: "Changing Resoluiton to 1280 x 1024 on nvidia."
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by DUNC4N on 2006-12-07
Hello all.

First I'd like to say, that I'm so excited to be up and running. I used automatix2 and it was so fast and easy.

Here's my question:

I've searched for the steps to change my resolution, but I think I'm missing somthing, or a certain step/command is assumed to be known.

I would like to change from 1024 x 768 to 1280 x 1024, and need step by step instructions please. (Still a newb)

Thanks in advance for the help.

-Dunc4n

AMD 4000
7900gt
74gb Raptor
2gb Ram

---

### Post by bodhi.zazen on 2006-12-07
please post the contents of /etc/X11/xorg.conf

In a terminal type:```
gedit /etc/X11/xorg.conf
```Cut and paste here.

Note: Linux is case sensitive x11 is not the same as X11 :p

---

### Post by taurus on 2006-12-07
You can add that resolution to /etc/X11/xorg.conf!  Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/X11/xorg.conf
```
Scroll down near the end where you will see a bunch of resolutions.  Just add "1280x1024" to the beginning of those lines.  Reboot and see if you can go to 
1280 x 1024...

---

### Post by DUNC4N on 2006-12-07
Ok, thanks, I will try as soon as I get home :)

---

### Post by crazedgremlin on 2006-12-07
Just checking the obvious here...

You have tried the gui, right?
it's in System -> Preferences -> Screen Resolution

---

### Post by DUNC4N on 2006-12-07
Yes. I will try the other instructions, when I get home. ;)

---

### Post by DUNC4N on 2006-12-07
> **taurus said:**
> You can add that resolution to /etc/X11/xorg.conf!  Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/X11/xorg.conf
```
Scroll down near the end where you will see a bunch of resolutions.  Just add "1280x1024" to the beginning of those lines.  Reboot and see if you can go to 
1280 x 1024...


Worked like a champ, added "1280x1024" before each set of res's, and on re-boot it was automatic. 

Thanks Alot.

-Dunc4n

---

### Post by taurus on 2006-12-07
You're welcome.

---

