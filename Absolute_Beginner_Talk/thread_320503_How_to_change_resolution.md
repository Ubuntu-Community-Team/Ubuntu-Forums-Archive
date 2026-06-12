---
title: "How to change resolution?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by XiaNo on 2006-12-17
Hey!

I've just installed ubuntu but the picture looks squeezed because i'm using a 16:10 widescreen. ](*,) 
How do I change the resolution?

---

### Post by taurus on 2006-12-17
You can modify /etc/X11/xorg.conf and include the refreshing rates and the desire resolutions you want...

Applications -> Accessories -> Terminal
```
sudo  cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak  <-- making a backup copy...
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by ddtrust on 2006-12-17
Check out this thread:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

(By the way, this was first search result in google using words ubuntu, screen, resolution as search words ;) )

---

### Post by XiaNo on 2006-12-17
> **taurus said:**
> You can modify /etc/X11/xorg.conf and include the refreshing rates and the desire resolutions you want...

Applications -> Accessories -> Terminal
```
sudo  cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak  <-- making a backup copy...
gksudo gedit /etc/X11/xorg.conf
```

Thank you very much, it helped :D :D

---

