---
title: "is there any way to run AWN dock without desktop effects on?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by irunwithknives on 2008-02-17
cause I cant use desktop effects with my ATI raedon express 200

---

### Post by MasterJS on 2008-02-17
I have that exact same card and I got Desktop Effects to work in Ubuntu Gutsy Gibbon (7.10) by installing the restricted driver from the Restricted Drivers Manager. Then I installed XGL ```
sudo apt-get install xserver-xgl
``` Then restart and you should have compositing. Which will allow you to use Compiz and AWN

---

### Post by irunwithknives on 2008-02-17
im sora afraid to do that cuz I installed that driver earlier today, and had to reinstall ubuntu cuz my computer wouldnt start up

---

### Post by JoshuaRL on 2008-02-17
Have you tried Envy?  Its a script to help you install the correct driver for nVidia and ATI cards.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by overdrank on 2008-02-17
Also you may look at cairo dock
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by irunwithknives on 2008-02-17
yeah-
i did-
it didnt do anything

---

### Post by irunwithknives on 2008-02-17
yeah-
it tells me

[COLOR="Red"]Error: Dependency is not satisfiable: cairo-dock[/COLOR]

---

### Post by irunwithknives on 2008-02-17
sorry im retarted
i figured it out
but I still want awn dock

---

### Post by irunwithknives on 2008-02-17
what does XGL do?

---

### Post by adam0s on 2008-02-17
I have the same card and I don't install the ati drivers because I want to be able to hibernate. So I'd like to know if awn would work with out desktop effects.

---

### Post by MasterJS on 2008-02-17
XGL is basically a workaround for the ATI cards that are not supported by the new ATI driver (almost all). It basically acts as a display on top of the normal one that allows compositing.

---

### Post by irunwithknives on 2008-02-17
if it screws me up, im blaming you

=P

---

### Post by overdrank on 2008-02-17
> **irunwithknives said:**
> what does XGL do?

HI and I just install cairo on my hardy system and use the xcompmgr  that is described in the link and works good. I think I may keep it. :)

---

### Post by MasterJS on 2008-02-17
back up your data so its not too bad

---

### Post by irunwithknives on 2008-02-17
okay
good thing I have my flash drive handy

those things have a knack for dissapearing

---

