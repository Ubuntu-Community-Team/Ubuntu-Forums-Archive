---
title: "Opera not working"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by de_battre on 2007-08-17
Hi i have just tried to install opera but when i open it i can't open a single page, it is like i am not connected to the internet at all (firefox and conqueror are fine). I first installed 9.23 from the opera site and then after reading a couple of threads here on the forums tried a 'static' package of 9.2 but had no luck with either. 

Any ideas what is going on? It has to be something simple. I am running feisty. The browser window opens fine but nothing will load.

cheers

---

### Post by de_battre on 2007-08-17
bump

---

### Post by misfitpierce on 2007-08-17
Should not have a problem... Try showing hidden folders in home directory and erasing the opera folder and reopening opera. :)

---

### Post by de_battre on 2007-08-17
[QUOTE=misfitpierce;3203996]Should not have a problem... Try showing hidden folders in home directory and erasing the opera folder and reopening opera.

Just tried this and it asked me to agree to the license agreement (which it didn't do before) but then same blank page and can't open anything....

---

### Post by Cappy on 2007-08-17
I think you may need to do this:
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by de_battre on 2007-08-17
> **Cappy said:**
> I think you may need to do this:
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

I do that in a terminal window? When i delete the ipv6 and try to type 'off' the 'o' doesn't work...

---

### Post by Cappy on 2007-08-17
```
gksudo gedit /etc/modprobe.d/aliases
```

---

