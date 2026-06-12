---
title: "Beryl Problems :("
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Simran on 2007-01-11
hi,

I installed beryl on my laptop, GFX card is: nvidia geforce 660 go. then after i rebooted i get an error before ubuntu loads 

"Failed to start X server (your graphical interface). It is likely that it is not set up correctly would you like to view the X server output to diagnose the problem."

Then when i hit "yes" i get

GDM: Xserver not found: /usr/bin/Xorg-air :0 :0 -auth
/var/lib/gdm/ :0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM

Then after that it says:

The X server is now disabled. Restart GDM when it is configured correctly.

don't really know where to start ? should i just format and re-install or .. ?

Thanks in advance

Simran

---

### Post by rsambuca on 2007-01-11
Try to reconfigure your xserver.

In the terminal enter the following code and answer the questions to reconfigure your xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Simran on 2007-01-11
thanks, i'll have a bash at it now

---

