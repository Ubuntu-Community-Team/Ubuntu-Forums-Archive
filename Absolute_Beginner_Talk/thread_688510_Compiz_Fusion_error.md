---
title: "Compiz Fusion error"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by G!zZm0 on 2008-02-05
I have an ATI accelerated graphic driver and I've already installed Compiz Fusion, Emerald but when I try to activate the visual effects it gives me an error saying:"The Composite extension is not available"...What do I need to do to fix this so that I can have my visual effects???

---

### Post by emarkd on 2008-02-05
Some ATI drivers require that you use xgl for rendering.  That's the xserver-xgl package in Synaptic.  Alternately, you may have some luck updating your drivers using [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by urmston on 2008-02-05
You also need to install python-opengl and freeglut3.  Both are in the repositories.

---

### Post by G!zZm0 on 2008-02-05
> **urmston said:**
> You also need to install python-opengl and freeglut3.  Both are in the repositories.


Thanks man!!!

---

### Post by G!zZm0 on 2008-02-05
Thanks man!!!

---

