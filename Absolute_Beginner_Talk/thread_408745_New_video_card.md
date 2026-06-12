---
title: "New video card"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2007-04-13
I put in a new video card into my Feisty box and x-server is not configured for it so i cant have grahpical login. I used to have a ati 9000 in there but it is now a Geforce 4, how do i reconfigure x?

---

### Post by taurus on 2007-04-13
Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure xserver-xorg
```
Make sure you pick **vesa** as a driver for your graphic card for now and once you have X running again, then install nVidia driver for it, using envy.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

