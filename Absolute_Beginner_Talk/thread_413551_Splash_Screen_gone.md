---
title: "Splash Screen gone"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Zzl1xndd on 2007-04-19
Hey guys I just upgraded one of my smaller systems from 6.06 to 6.10 and now I have no splash screen. Everything else seems to be working normally, when the splash screens should come up on start up and shut down I just get a blinking curser in the top left hand corner of the screen.

---

### Post by Kobalt on 2007-04-19
Do you have the *uspash* packages installed ?
You might want to check this out through Synaptic...

---

### Post by Zzl1xndd on 2007-04-19
yeah it is installed

---

### Post by Kobalt on 2007-04-19
What does your usplash conf file say : ```
cat /etc/usplash.conf
```

---

### Post by Zzl1xndd on 2007-04-19
# Usplash configuration file
xres=1152
yres=864

---

### Post by Kobalt on 2007-04-19
Is it a resolution your screen support ? 
If not, you can change it to something like 1024/768, or 800/600...

---

### Post by Zzl1xndd on 2007-04-19
still the same

---

### Post by Zzl1xndd on 2007-04-20
the splash on shut down comes up if I set it at 640 by 480 but still not on start up.

---

