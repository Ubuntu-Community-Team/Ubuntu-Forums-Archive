---
title: "is it possible to edit configuration files in a livecd?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Gustavo on 2006-08-19
Let's say that I want to edit /etc/resolv.conf, /etc/X11/xorg.conf or something like that. It can be done if I'm using a livecd?

Regards,

Gustavo

---

### Post by &#12465;&#12452;&#12488; on 2006-08-19
I assume you can do it, but the config won't be saved after you've shut down the system.

---

### Post by GeekSpeek'r on 2006-08-19
yes, but its temporary (lasts until reboot -- I think)

sudo vi /etc/resolv.conf

---

### Post by az on 2006-08-19
You can also install packages, if you have enough ram.

I think that those packages will then get installed along with the base system if you then click on the install icon.

---

### Post by GeekSpeek'r on 2006-08-19
it is still temporary..........

---

### Post by Gustavo on 2006-08-19
Ok, thanks! ;)

---

### Post by IYY on 2006-08-20
Don't forget that these are root-owned files, so the command to edit them with gedit would be:

```
gksudo gedit /etc/X11/xorg.conf
```

---

