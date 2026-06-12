---
title: "How do I know if a driver is properly installed?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-11
I installed the ATI closed-source drivers, and I think I did it correctly.  I know they aren't the best, but I thought I'd give them a try since I'm pretty to new linux and they had an automatic installer.  If they don't work out I'll change to the open-source drivers.  Unfortunately, I don't even know if they ARE installed correctly; is there a way I could tell?  A benchmark or something?

---

### Post by sad_iq on 2007-08-11
Try ```
glxinfo | grep direct
``` if it says Direct Rendering yes then you have the drivers installed

---

