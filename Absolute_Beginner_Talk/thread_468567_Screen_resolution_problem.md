---
title: "Screen resolution problem"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by chuugokujin on 2007-06-09
I got my ATI X850 drive installed, but whenever I change my /etc/X11/xorg.conf to set up my
resolution to over 1024x768 or make the color deeper than 24, the system goes to black screen next time reboot. I think it is the problem of my monitor, Samsung 920n.
Could anyone help me?

---

### Post by Brightbelt on 2007-06-09
Hi,
I don't think it is your monitor's problem. Check out this software [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) . This is the only way I've been able to somewhat successfully install my X-1650 ATI driver. 

Strangely enough, when I use this and reboot, I get a blank screen, BUT, if I reboot and choose a different kernel, the ATI seems to be installed successfully.  Thus I install it on one kernel and use another kernel.

For some, it has worked all the way. So it's hard to tell and depends on the system. 

I hope this helps, ..Frank B.

---

### Post by kyphi on 2007-06-09
I got my ATI X850 drive installed

Do you mean 'graphics card'?

In a terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```
on the resulting menu, use your up/down arrows to find the resolution you want, then press the spacebar, then enter, then exit.

Reboot.

---

### Post by Bo0ddha on 2007-06-09
Figured it out.  Thanks!

---

### Post by chuugokujin on 2007-06-09
Thanks a lot guys!

---

