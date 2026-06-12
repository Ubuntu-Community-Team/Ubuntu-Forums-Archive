---
title: "Font path problem X wont start!"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by glaze0101 on 2008-01-18
Something keeps happening when I try to install fonts.  I had all of these fonts installed on Feisty before I upgraded to Gutsy with no problems.  Now everytime I try to install the fonts (off a cd mostly truetype) X crashes after a while and the only way I have found to get back in is by creating a new user.

This time I cant even get to the place where it asks for my usr name and pwd. 

So I rebooted in recovery mode and then typed in startx

I got back errors about fonts:

Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

then it says:
waiting for X server to shut down (EE) intel (0): I830 Vblank Pipe Setup failed 0
(EE) intel (0): I830 Vblank Pipe Setup failed 0
(EE) intel (0): I830 Vblank Pipe Setup failed 0
.FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

Can anyone help me get X back???

---

### Post by nikoPSK on 2008-01-18
try ```
startx
``` if not, let's reconfigure x ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Best,
nikoPSK

---

### Post by glaze0101 on 2008-01-18
I reconfigured X as suggested and then tried startx again, same problem. no change

---

### Post by glaze0101 on 2008-01-18
/bump

---

### Post by nikoPSK on 2008-01-18
> **glaze0101 said:**
> /bump

please don't bump until at least a day has gone by. :)

---

