---
title: "grep question"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-09-21
isnt there a way to lsmod | grep to see if 3d acceleration is turned on?

---

### Post by szf on 2006-09-21
Might you be thinking of:

[FONT="Courier New"]$ xdpyinfo | grep GLX[/FONT]

--or--

[FONT="Courier New"]$ glxinfo | grep direct[/FONT]
?

---

### Post by swp6499 on 2006-09-21
it ssys direct rendering is on and yes to glx and sgi glx

---

### Post by szf on 2006-09-21
Then AFAIK, you're golden...

---

### Post by swp6499 on 2006-09-21
thank you

---

