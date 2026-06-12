---
title: "no top bars in compiz"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-20
i just loaded beryl manager when i use compiz the top bars of windows i open vanishes...
why is it can it be fixed

---

### Post by AriciU on 2007-06-20
This fixed it for me in Beryl

> sudo nvidia-xconfig --add-argb-glx-visuals

Then ctrl+alt+backspace to restart the x server.

Don't know about compiz but it might fix it for it too.

BTW... you must have the Nvidia drivers installed and enabled (Enable nvidia driver option somewhere in Gnomes menu's)

---

### Post by pardesi on 2007-06-20
thanks but  use ATI any idea how to set that right in it

---

### Post by Rui Pais on 2007-06-20
hi, 
try to add it by hand. 
Edit /etc/X11/xorg.conf and add the line
```
 Option      "AddARGBGLXVisuals" "True"
```
at Section "Device" under the  Driver line for your graphics card.

hth

---

### Post by pardesi on 2007-06-20
thanks....:D

---

### Post by lamalex on 2007-06-20
> **pardesi said:**
> thanks....:D

did that work? I have that problem in compiz but not beryl, I prefer beryl anyway but it'd be nice just to have it working.

*EDIT*: it did not fix it.

---

### Post by sailor2001 on 2007-06-20
I have that problem in beryl after running it for a while..the id bar just disappears. Rebooting beryl sets it back again

---

### Post by pardesi on 2007-06-20
no even i have this problem in compiz(till now:mrgreen:) not in Beryl

---

### Post by pardesi on 2007-06-20
> **Iamalex said:**
> did that work? I have that problem in compiz but not beryl, I prefer beryl anyway but it'd be nice just to have it working.

*EDIT*: it did not fix it.
it worked in Beryl...:D

---

