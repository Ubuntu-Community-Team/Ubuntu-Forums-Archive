---
title: "[SOLVED] Visual Effects"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by short3000y on 2007-12-09
ok i have ubuntu 7.10 and when i try to enable visual effects i get a error:::

:("The Composite Extension Is Not Available":(

is there any way to fix this? of will i just have to live without visual effects.... please help, i wanna try out some visual effects!!!!! 

thanks,
~Nate

---

### Post by SunnyRabbiera on 2007-12-09
hmm, do you use any special video cards or have low memory specs?

---

### Post by short3000y on 2007-12-09
i have 2gigs of memory and have an ATI MOBILITY RADEON 1400 video card...

---

### Post by short3000y on 2007-12-09
can ANYONE help me????

---

### Post by Ub1476 on 2007-12-09
I have the same graphic card as you. Works brilliant:)

First, make sure to check the sources System>Administration>Software sources (do not check "source code").

After that, assuming you have installed the driver for your graphic card, install XGL and Advanced Desktop Effects:

```
sudo apt-get install xserver-xgl compizconfig-settings-manager
```

Logout and login, set Visual Effects to custom, open System>Preferences>Advanced Desktop Effects and have fun! :)

---

### Post by short3000y on 2007-12-09
thanks that fixed it!!!!!!

---

### Post by SunnyRabbiera on 2007-12-09
I figured that was the case, sometimes video cards mess with this sort of thing

---

### Post by short3000y on 2007-12-09
I <3 my visuals now that i have them!!!!!!!

---

