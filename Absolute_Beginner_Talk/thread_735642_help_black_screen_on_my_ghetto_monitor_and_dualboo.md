---
title: "help black screen on my ghetto monitor and dualbooting"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by marine63 on 2008-03-25
hello, Ive read some of the articles on cases that have the same symptoms  of my problems. After Ubuntu it turns black. when i just installed ubuntu 7.04 and after ubuntu loads the light on the monitor turns from blue to red... I get the same problem when I 1st used this monitor for XP. I solved this problem by using my old HP M90 19 inch to install newest drivers and set refresh rate to 60 like the manual said to... After I recalled this from my memory I replaced my ghetto X2gen mw19r with my m90 and upgraded my 7.04 to 8.04 (Which I love !!) and used the restricted drivers for my foxconn geforce 8800gts oc I set resolution to 1280 X 960 like my windows xp's and the refresh rate was default ( what is the default refresh rate of ubuntu? i think it have to be 60 in order to work...) And yes my monitor is sh*tty and thank goodness that X2gen became bankrupt!!! >:( anyways if theres any thing i can do about this problem please inform me and please save me from the evil clutches of microsoft!

I have a problem with boot manager as well. Im using acornis os selector... I remember i was able to make it boot manager with out acornis. acornis gives a gui and when i click on what i want to boot to it was me again in text... ( windows boot manager / grub maybe?) how do i make it so ill only ask me once... If i need to use grub or gag please tell how to install them :( thx.

---

### Post by dstew on 2008-03-26
Does the old monitor work at all? I guess you get the Ubuntu splash screen, but then blackness, right? If so, you may need to reconfigure the Xserver to get a useable display. Settings that work with one monitor might not work at all with another, especially at high resolution.

I recommend doing```
sudo dpkg-reconfigure xserver-xorg
```and settling for a lower resolution. You might also just use the vesa driver to get a functional (but clunky) desktop.

---

### Post by marine63 on 2008-03-26
yes my old m90 works with ubuntu 7.10 and 8.04 well... b/c my new lcd is a spaz when it comes with old drivers and resolution and refresh rate 
ty for responding~!

---

