---
title: "Screen Resolution Problem..."
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by medic on 2007-06-03
i m having a strange problem with Feisty Fawn...
i hav Dual Core with 945 Gcc...
When i start the computer sometimes ubuntu starts with 1024 x 768 and sometimes it starts with 640 x 480..
When i go in resolution setting it dont even show these 1024 x 768 resolutions...
then the only option is to restart and after restarts into 1024 x 768 ...
Wat is the problem with it??

---

### Post by coffeecat on 2007-06-03
Is the monitor switched off or disconnected when you get 640x480? In Ubuntu (this was in Dapper or earlier - I haven't tried this in Feisty) , if the xserver can't detect a monitor it will default back to the lower resolution.

I found this out by accident when I booted up Ubuntu while working on another computer through my KVM switch.

---

### Post by medic on 2007-06-03
> **coffeecat said:**
> Is the monitor switched off or disconnected when you get 640x480? In Ubuntu (this was in Dapper or earlier - I haven't tried this in Feisty) , if the xserver can't detect a monitor it will default back to the lower resolution.

I found this out by accident when I booted up Ubuntu while working on another computer through my KVM switch.

No monitor isn't switched off...
It just goes into lower and higher resolution randomly...

---

### Post by coffeecat on 2007-06-03
> **medic said:**
> No monitor isn't switched off...
It just goes into lower and higher resolution randomly...

The xserver has two ways of setting things up as it starts. The 'old' way is by using the settings in the configuration file /etc/X11/xorg.conf. As newer versions of xserver get developed, they are more and more using data they gather by probing your hardware. The eventual ambition, I believe, is to be able to do without xorg.conf

If it randomly goes into higher or lower resolutions, I very much doubt this is an issue with the xorg.conf file - it simply doesn't rewrite itself randomly. Which leaves the physical connection with the monitor. OK, you didn't have the monitor switched off, but this unusual behaviour sounds like a problem somewhere between the graphics card, through the connection itself to the monitor.

Is there any possibility of you borrowing/using a different monitor for a while to see if you can reproduce this problem? Is there anything unusual about the connection between the computer and the monitor?

---

