---
title: "Oh my, I've really done it now. Can't start X"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Esben Kramer on 2006-10-31
I installed the Nvidia-settings, which removed all my beloved nvidia and xserver-packages it seems. I installed the nvidia-glx drivers again, and now I can't start X. The error-display is blank. I can edit my xorg.conf when in recovery-mode, but it does nothing. Any suggestions?

---

### Post by meng on 2006-10-31
Have you tried:
sudo dpkg-reconfigure xserver-xorg

and choosing 'nv' as the device driver? You could try 'nvidia' also, but 'nv' may be the safe first option.

---

### Post by Esben Kramer on 2006-10-31
I'm gonna go try the reconfigure-thing right away. Crossing my fingers. Thanks...

---

### Post by slimdog360 on 2006-10-31
meng is right, that should work. But if you cant just edit the part in your xorg.conf file where is says "nvidia" to "nv". It should be in the display section, the quotes will be part of it too.

---

### Post by Esben Kramer on 2006-10-31
I tried sudo dpkg-reconfigure xserver-xorg, but it told me that xserver is either broken or not installed...that makes more sense, since it never even seems to get to the xorg.conf-file. How do I make a reinstall of X from safemode?

---

### Post by slimdog360 on 2006-10-31
sounds like you may have deleted X.
```
sudo apt-get install xserver-xorg
```

---

### Post by John.Michael.Kane on 2006-10-31
Have you tried running sudo dpkg-reconfigure xserver-xorg

---

### Post by Esben Kramer on 2006-10-31
Weee. Up and running again. Thanks! Now to get that tv-out thingie working...

---

