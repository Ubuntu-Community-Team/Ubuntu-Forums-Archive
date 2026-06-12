---
title: "Elementary OS Installation Issues"
date: 2013-06-07
forum: Any Other OS
---

### Post by CursedWithin on 2013-06-07
Hey guys, I need some help with installing beta 2 version of Elementary OS Luna.

Whenever I try to install Elementary from a CD, it always gets  stuck at the Elementary "e" logo. Nothing happens after that. I tried  installing the OS with nomodeset, and it worked for a while. After I  restarted the computer when the battery was down, the installation  stopped working again.

Does anyone know how I could fix this?

---

### Post by vadimkolchev on 2013-06-07
What do you mean - worked for a while? Did you manage to install it or not? It is the working installation that doesn't work or installation disc?

---

### Post by CursedWithin on 2013-06-07
> **vadimkolchev said:**
> What do you mean - worked for a while? Did you manage to install it or not? It is the working installation that doesn't work or installation disc?

I managed to get past the Elementary logo. When I was about to install Elementary OS, my computer got shut down due to its battery. I plugged the cable and turned the computer back on, but when I did, I got stuck in the Elementary logo again.

---

### Post by vadimkolchev on 2013-06-07
You said you succeeded with passing nomodeset argument. Could you try it again? And also, if you have to pass nomodeset during installation, there's a big chance that your video card may be not very well supported by this distro and you may end up with cli. Usually in most user-friendly distros video card is detected on boot of the installation media and proper driver is loaded. In your case something is wrong with the driver of the installation media, probably, or with compatibility of distro and your video card. However, you could try if you wish.

---

