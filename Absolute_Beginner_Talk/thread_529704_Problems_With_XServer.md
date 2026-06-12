---
title: "Problems With XServer"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by derouge on 2007-08-19
Okay, here's the issue. I did a clean install of Feisty Fawn today. Everything seemed to have went fine. I go to boot it and  ... blank screen. Gah!

So I booted in "Recovery Mode" and did "dpkg-reconfigure xserver-xorg" using the "i810" driver. Started X using "sudo startx" and wah-lah! Loads up fine. Everything looks good so I shut the system down and tried to boot in normal load. It gets stuck on the same blank screen.

Why is this, and what's the solution? Oh, and I tried the Vesa drivers since I read they were general. Didn't work at all, X failed to start.

---

