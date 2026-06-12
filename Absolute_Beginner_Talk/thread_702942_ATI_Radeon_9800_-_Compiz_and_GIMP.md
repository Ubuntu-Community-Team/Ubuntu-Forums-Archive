---
title: "ATI Radeon 9800 - Compiz and GIMP"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by ylwsub68 on 2008-02-20
I looked for other similar forums regarding this problem, but to no avail, so here's what's going on.

I have an ATI Radeon 9800 card, and I downloaded the Linux package of the latest drivers from the ATI site and installed them. BEFORE I installed them, Compiz was working some (I had wobbly windows and Ctrl-Alt-Down Arrow worked). But since I "installed" the drivers, I haven't been able to enable desktop effects.

Also, I've been using GIMP and it updates the picture really slowly when I change something (like adjusting levels) by "scanning" it from top to bottom. I don't know if this is supposed to happen, but it's still quite annoying. Also, if I do any graphically intensive work in GIMP (like layer masks on full-sized photos), the image starts to mess up, like pieces of the image will appear in different parts of the image when they're not supposed to.

Thanks in advance.

---

### Post by spiderbatdad on 2008-02-20
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by ylwsub68 on 2008-02-20
Ok, I followed that guide, and I tried to turn desktop effects and it says "The Composite extension is not available." And GIMP still behaves the same way.

---

### Post by spiderbatdad on 2008-02-20
Haven't seen that particular error. Have you installed compizconfig-settings-manager from synaptic?
Looks like you need xorg-driver-fglrx or xserver-xgl as well. It is experimental software, so you can't expect perfection. Not sure what's wrong with gimp, other than using it in a composite environment.
You might like a tool like compiztray-icon or gnome-compiz-manager to help manage the environment...turn it on and off easily. Sorry I couldn't be of more help.

---

### Post by ylwsub68 on 2008-02-20
I installed all that stuff you said. And now it works perfectly! Thank you very much. :-)

---

