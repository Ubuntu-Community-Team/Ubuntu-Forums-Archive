---
title: "Checking and Installing OpenGL"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-04-09
How do I know if I have OpenGL installed and configured correctly?  I´ve tried playing some games in wine but they´re extremely slow and I think its because I dont have opengl.

---

### Post by chalex on 2007-04-09
Try the command "glxinfo".   or  "glxinfo |grep OpenGL"

---

### Post by Brucey on 2007-04-09
libGL warning: 3D driver claims to not support visual 0x4b

Thats one of the lines it gives me.  Should I be worried?

---

### Post by mcduck on 2007-04-10
If you have OpenGL games, you have OpenGL. You can't install one without getting the other as long as you use Ubuntu's package management. And OpenGL is installed by default anyway.

More likely you are having troubles with your graphics card drivers..

---

### Post by igknighted on 2007-04-10
> **Brucey said:**
> libGL warning: 3D driver claims to not support visual 0x4b

Thats one of the lines it gives me.  Should I be worried?

Looks like you are using an ATI card with the default drivers.  If you install the fglrx drivers (the ATI proprietary ones) from synaptic or through apt then you will get much better performance in gaming.

If you are using an Intel or some other onboard chip you might need a new graphics card to improve performance.  Please also remember that most games will run extremely poorly through wine, so your system might be fine, wine just cant render it that well.

---

