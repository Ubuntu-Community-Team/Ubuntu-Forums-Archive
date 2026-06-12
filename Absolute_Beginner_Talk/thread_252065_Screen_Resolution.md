---
title: "Screen Resolution"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by debasishg on 2006-09-06
suddenly my screen resolution is appeared as 640x480 when i started in my other machine. but till morning it was 1074x. how do i restore the resolution. From the screen resolution menu, it was not happening.

thanks in advanced

---

### Post by jd65pl on 2006-09-06
Have you tried restarting.

if that doesn't work try

```
dpkg-reconfigure xserver-xorg
```

---

### Post by bruce89 on 2006-09-06
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
is much better than the above command, as it skips all the steps apart from the resolution screen.

Then press Control+Alternate+Backspace to restart X.

---

### Post by debasishg on 2006-09-06
Thank you guys .... i have got lots of help from you and its really appreaciable.

---

### Post by debasishg on 2006-09-07
Not working..... its restarted and resuming the same resolution.

---

### Post by aeiah on 2006-09-07
perhaps the driver for your graphics card has been set back to the default one in the configuration file. did you make a backup when installing your graphics card drivers?

---

### Post by debasishg on 2006-09-07
no i didn't. i have installed in two diff machines, one has nVIDIA GC and another has 915 intel chipset. the first one is ok but 915 one is having the resolution problem. what should i do now? should i have to re-install it again?

---

### Post by bodhi.zazen on 2006-09-08
Did you update or install anyting?

If not, try editing /etc/X11/xorg.conf and reducing the default color depth to 16
```
Section "Screen"
    Identifier  "XXX"
    Device      "XXX"
    Monitor     "XXX"
    DefaultDepth 16......
```

Do not edit the XXX.

---

### Post by debasishg on 2006-09-08
Still not working.... don't know what i have to do. i have seen my another xorg.conf but all are fine [??].

---

### Post by bodhi.zazen on 2006-09-08
First the obvious... Have you re-started X since editing xorg.conf.

If so would you post your xorg.conf and monitor.

---

### Post by debasishg on 2006-09-10
i have uninstalled ubuntu and installed Mandriva and its working fine. i have tried with drapper also, but not satisfied with the resol. i think my HP machine has some bugs as i have failed to installed FC3/4 and RHE9 workstation.

---

### Post by bodhi.zazen on 2006-09-10
> **debasishg said:**
> i have uninstalled ubuntu and installed Mandriva and its working fine. i have tried with drapper also, but not satisfied with the resol. i think my HP machine has some bugs as i have failed to installed FC3/4 and RHE9 workstation.

Congradulations.

---

