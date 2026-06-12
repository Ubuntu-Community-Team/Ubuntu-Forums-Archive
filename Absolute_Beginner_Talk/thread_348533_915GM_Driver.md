---
title: "915GM Driver?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by knvb1123 on 2007-01-28
Hello,
I am a nerd but not enough to compile my own drivers...
I am running Ubuntu 6.10 and I have 915GM chipset...
I am stuck with 1024x768... on my windows, because there is a driver, i get upto 1240x800...
How do I get a driver for this chipset to allow to me to go to 1240x800 resolution?
Is that possible?

Also, I ONLY get one resolution of 1024x768... How can I go lower? higher?

Thank You...

If I can get this by means of very complicated methods, I am willing, I just need to learn it. :) 

Thanks!
knvb1123

---

### Post by taurus on 2007-01-28
Maybe this guide helps.

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

And if you want to add other resolutions, you can add them to /etc/X11/xorg.conf.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by jordanmthomas on 2007-01-28
Also, as a side note:  1240x800 is not standard.  You might want to make sure it wasn't something like 1280x800

---

