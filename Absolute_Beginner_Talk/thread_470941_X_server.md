---
title: "X server"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-11
Hi, i installed ubuntu 7.04 on my new laptop, and then i installed my screen card (Nvidio GeForce go 7300 400 Mb) with Envy. And now when i try to start the computer i get the messegde that x server has failed and i can't start Ubuntu........HELP
Since ubuntu won't work i am forced to be on Vista, and i hate vista. thanks for all answers

---

### Post by EndPerform on 2007-06-11
Have you updated lately?  If so, it might have updated your kernel, which you would then need to re-install the drivers for your video card.

---

### Post by taurus on 2007-06-11
Boot into recovery mode from GRUB menu and reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```
Just **vesa** driver for your graphic card for now and once you get X up and running again, you can install nVidia driver for it as described in this guide.

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

