---
title: "Screen resolution problems"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by brummygem on 2006-10-23
I know that you are probably sick of the times this nugget has come up but, here it is again:-? .  I am a complete newby to ubuntu and linux but I am feeling my way slowly.  I managed to get a dual boot system installed on my HP Pavilion 404UK. Got Opera as by browser:) and sorted my email out. The one thing that's bugging me is the screen resolution. It's currently set at  1280 x 1024.  Too small for my ageing eyes.  I would like to set it at 1024 x 768 but it won't let me.  Well it will change but as soon as I hit 'apply', the screen flashes and returns to the log in screen, resolution unchanged](*,).  Can someone please walk me through a solution:-k :confused:.  Thanks, in anticipation

---

### Post by madmetal on 2006-10-23
you can change the resolution by editing xorg.conf
open a terminal and type
sudo gedit /etc/X11/xorg.conf
give your password and change the resolution to the ones you want(and your monitor and vga support)
do you have the vga driver installed? if not install the vga driver first.

---

### Post by CatKiller on 2006-10-23
> **brummygem said:**
> I would like to set it at 1024 x 768 but it won't let me.  Well it will change but as soon as I hit 'apply', the screen flashes and returns to the log in screen, resolution unchanged

Does the same thing happen if you choose a lower refresh rate for your 1024x768 resolution before you hit Apply?

---

