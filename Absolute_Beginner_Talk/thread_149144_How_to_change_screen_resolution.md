---
title: "How to change screen resolution?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by vzdesic on 2006-03-23
How to change screen resolution on my Ubuntu 5.10?
Vedran

---

### Post by Antrix on 2006-03-23
I believe the best way to do this is to modify your /etc/X11/xorg.conf file, save changes & then restart X. 
xorg.conf is the configuration file for the X server.

I haven't got time to explain exactly how to edit it (doing an essay), but it should be pretty self explanatory.

Perhaps somebody else can give you a more detailed answer, or maybe even inform you about a GUI tool that will modify the xorg.conf for you.

I'm not running ubuntu right now (windows xp), but will be back on linux within the week.

Good luck.

---

### Post by Chyper on 2006-03-23
System > Preferences > Screen Resolution

---

### Post by njzillest on 2006-03-23
i highly suggest you first go to system and change it first. If it is locked then you will need to edit your Xorg file. But make sure you back up your original, or else you will screw up the resolution permently just like me.

---

### Post by njzillest on 2006-03-23
wget /etc/X11/xorg.conf (or atleast from my knowlege thats how you do it)

in the terminal

---

### Post by akiro.yamamoto on 2006-03-23
It's 
```

sudo gedit /etc/X11/xorg.conf

``` 
Then you should find a section like this and enter the resolutions you want enabled. See pic.
Then you can select your resolution from :
System >> Preferences >> Resolution
See pic...
Hope this info helps ;)

---

### Post by vzdesic on 2006-03-24
Thanks.

---

### Post by akiro.yamamoto on 2006-03-24
[quote=vzdesic]Thanks.[/quote]

De nada :mrgreen:

---

### Post by Yaksha on 2006-03-24
thanks that helped me alot to!^^

---

