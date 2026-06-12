---
title: "Beryl + Nvidia"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-12-28
When I try to run beryl-manager I get something like:
```

greyson@greyson:~$ beryl-manager
greyson@greyson:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present

```
And then the screen goes all weird and I have to restart X
How can I fix this?

---

### Post by kelbizzle on 2006-12-28
make sure you have the drivers installed correctly. 
If you type: glxinfo | grep direct

It should say direct rendering "yes"

---

### Post by greyash99 on 2006-12-28
it says yes

---

### Post by kelbizzle on 2006-12-28
Post your xorg.conf file please :-D

---

### Post by PriceChild on 2006-12-28
Please say you're running Edgy, then [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

