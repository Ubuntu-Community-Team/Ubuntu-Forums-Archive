---
title: "beryl on ATI radeon 200...help?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by ZeldaFreak on 2006-12-28
i have installed drivers for my ATI radeon xpress 200, i have direct rendering and everything seems to be working, apart from a small problem with beryl, i get this when i start up beryl:

XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension


what do i do?

anything useful appreciated. thanks

---

### Post by ZeldaFreak on 2006-12-28
Bump...

---

### Post by ZeldaFreak on 2006-12-28
Bump...

---

### Post by ZeldaFreak on 2006-12-28
does anyone know..? :(

---

### Post by ZeldaFreak on 2006-12-28
*sigh*

---

### Post by ZeldaFreak on 2006-12-30
Bump

---

### Post by rlozano on 2006-12-30
> **ZeldaFreak said:**
> i have installed drivers for my ATI radeon xpress 200, i have direct rendering and everything seems to be working, apart from a small problem with beryl, i get this when i start up beryl:

XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension


what do i do?

anything useful appreciated. thanks

unfortunately, X200 is not 3D capable and Beryl will not work with it. :-) it's the same video card i have in one of my laptops... X300 and up will work with Beryl, but not X200. 

hmmm.... maybe you can forget beryl for the meantime.... :-k

---

### Post by ZeldaFreak on 2006-12-30
*sigh*... well i was thinking of getting a new graphics card anyway..](*,)

---

### Post by quiquoqua on 2006-12-31
Wait man... you can make beryl work!

i have the same card and it took me many hours to solve the problem, but maybe now i did it.

i'll explain in a long way, to make sure that it will be clear.

to make beryl work, you must have a working AIGLX or XGL environment: those are extensions that work in your display to use 3d acceleration capabilities. AIGLX is more capable as performance, because has a more intelligent use of your gpu capabilities, but needs some features that can be given only by the DRI implementation of your X server: and **as now** the x200m support by the open source driver / included in Xorg / is broken. so: you cannot use AIGLX to make beryl work; you must switch to xgl. Xgl is another way to use your gpu capabilites on your desktop, and it may use the aopen source drivers included in Xorg, and furthermore the proprietary ati driver. The proprietary Ati driver are unusable with aiglx, but do their work with X and Xgl: this means you can get 3d acceleration for your card in linux. Until now, a lot of threads spoke about ati driver compatibility and walktrough for x200m, but it seems that a lot of issues with our card had been solved with the 8.32.5 release of the proprietary driver. it worked for me, even tough i'm still having problems with beryl. but i think that is a code issue, that can be resolved by the community and anyway less problematic than the driver issue. i have an hp dv8000 laptop with ubuntu edgy amd64 on it. i can get to work games like sorched3d and i can launch fgl_glxgears with success.

---

### Post by ZeldaFreak on 2007-01-02
ok, thanks!;)

---

