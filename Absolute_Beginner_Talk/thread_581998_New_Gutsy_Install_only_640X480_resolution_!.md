---
title: "New Gutsy Install only 640X480 resolution !"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-10-19
Just did a clean install, vs the upgrade to Gutsy I had, but now I only have the 640X480
resoulution available ! Attempted Envy,but the resolution is so big, I can't access the
action buttons !

---

### Post by useResa on 2007-10-19
Just guessing ... but do you have an nvidia card?
I had the same issue. Temporarily switched to "nv" driver instead of "nvidia". This gave me sufficient resolution to use Envy.

---

### Post by Drakkor on 2007-10-19
Thanks, please explain how to switch to "nv" driver instead of "nvidia"

---

### Post by Drakkor on 2007-10-19
Thanks, please explain how to switch to "nv" driver instead of "nvidia"

---

### Post by Drakkor on 2007-10-19
bump

---

### Post by duruttye on 2007-10-19
Hey. You can do that by reconfiguring xserver xorg.

reboot, before u log in, select failsafe terminal, then type:

sudo dpgk-reconfigure xserver-xorg

u wiil see a blue screen asking stuff, at one point you have to select the video driver for your card, before the nvidia, there is the nv. After a few more questions there will be a table for you o select the resolutions u want.

I'm not sure this will help, but I would definitely try it.

And by the way, I have to do this every second time I reboot in Gutsy...

---

### Post by duruttye on 2007-10-19
OOOH, sorry, there is something new in Gutsy!!!

System - Admin - screens and graphics. You can mess around there to, without using the terminal.

Good luck!

---

### Post by buntunub on 2007-10-19
:popcorn:

---

### Post by Drakkor on 2007-10-19
:( Tried all the responses, tried envy,tried restricted drivers. edited nvidia to nv in xorg.conf and I was able to get the proper resolution,but everytime  i tried to execute restricted drivers it went back to 800x600, Well I'm glad that I still have the upgraded Fiesty/Gusty
install, everything works perfect in that !!

---

### Post by bruce89 on 2007-10-19
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Drakkor on 2007-10-19
@bruce
Yeah, I don"t know if that"ll work cause in safe mode, I tried sudo dpgk-reconfigure xserver-xorg and it came back  sudo dpgk-reconfigure / command not found.

---

### Post by Zero7 on 2007-10-19
Do you have onboard graphics and nVidia in your system? I had the same issue with that config.

---

### Post by Drakkor on 2007-10-19
I have a Nividia GF4 TI4200 128mb pci card. , and all this resolution,and restricted drivers,and CompizFusion stuff runs fine with the Gutsy upgraded Fiesty !

---

