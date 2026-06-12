---
title: "missing buttons from the windows on ubuntu 7.10"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ken-kenshin on 2007-11-16
hi a lot of my windows buttons have diapered the minimize and maximize buttons are not on my windows to get out of them i am useing the 7.10 ubuntu desktop 
and my terminal is not working ether it just i a white box what can i do about this what will fix it 
i just install 7.10 and it was working before it started when I installed wine a few days ago

---

### Post by approaching on 2007-11-16
something similar to this will happen if you are messing around with compiz, specifically emerald. but it would look more like the entire windowing would be gone (title bar, max, min, close, and edging). if that sounds like you, just restart x (ctrl+alt+backspace).

---

### Post by ken-kenshin on 2007-11-16
i havent messed wiht any thing on it just install wine on it

---

### Post by Surkow on 2007-11-16
Open xorg.conf (located at /etc/X11/xorg.conf) and add 	```
Option		"AddARGBGLXVisuals"	"True"
```to  section "Device".

---

