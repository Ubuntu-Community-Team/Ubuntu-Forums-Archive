---
title: "Resolution"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-01-01
i have ubuntu on a dual boot with windows 2000, everything in ubuntu was working fine but when i went back to windows the resolution was messed up and after i fixed that, when i came back to ubuntu the resolution was on 640x480 and the drop down box for changing the resolution wont come down

---

### Post by Mustard on 2006-01-01
Try this in terminal

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the default options for anything it asks you that you don't know the answer to.  When you are finished, hit Ctrl-Alt-Backspace to restart the X server.

---

### Post by notquitehere188 on 2006-01-01
thanks, it works better than before now :)

---

### Post by Mustard on 2006-01-01
[QUOTE=notquitehere188]thanks, it works better than before now :)[/QUOTE]
That's good to hear. :)

---

