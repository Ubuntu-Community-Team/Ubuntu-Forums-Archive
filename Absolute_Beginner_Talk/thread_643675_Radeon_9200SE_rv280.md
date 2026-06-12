---
title: "Radeon 9200SE rv280"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by nirishmodi on 2007-12-18
I am a completely first time user to Linux and my first choice for Linux was UBUNTU.
I am having a ATI Radeon 9200SE (RV280) AGP 128 MB Graphics Card. When I was using my VGA port of my graphics card then the UBUNTU progress bar hangs at a particular point and when I changed it to my onboard graphics (i.e. of my motherboard) then the complete OS works fine. I have checked that my graphics card and it is working absolutely fine. What should I do. I am running UBUNTU Gutsy 7.10. I have tried ENVY but it says that _ATI's Legacy Driver does not support your operating system_. What should I do??

---

### Post by MangasColoradas on 2007-12-18
Check my sig link for ATI...it might help.

[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

---

### Post by nirishmodi on 2007-12-18
Restricted Driver Manager Says:
_your Hardware Does Not Need Any Restricted Drivers. _

---

### Post by Paqman on 2007-12-18
I used to use a 9200SE with no restricted drivers and it was fine, never had any problems with it. I was using VGA not DVI, though.

---

### Post by nirishmodi on 2007-12-18
Can you tell me the procedure of installing the drivers for the VGA port.

---

### Post by spiderbatdad on 2007-12-18
maybe...```
sudo apt-get install xorg-driver-fglrx
```

```
aticonfig --initial
```

---

### Post by nirishmodi on 2007-12-19
Please send me a solution to my problem. It is eating me from within.

---

### Post by nirishmodi on 2007-12-20
Actually UBUNTU is detecting my graphics card but I am not able to switch over to it.

---

