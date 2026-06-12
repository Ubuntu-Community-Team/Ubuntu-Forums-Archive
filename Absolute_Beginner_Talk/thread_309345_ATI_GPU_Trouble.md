---
title: "ATI GPU Trouble"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by sindrum_murdnis on 2006-11-29
Okay just recently i purchased a killer ATI X1600 GPU. The damn thing seems to work just fine with my windows hard drive but wouldn't allow Ubuntu to start or Ubuntu wouldn't let Ubuntu to start. Anyways so me being me reinstalled Ubuntu and it worked :) . So i spent a few hours setting up Ubuntu, reading setting up reading setting up(you know the deal). After i set it up the thing worked great(by the way i used the ATI drivers that came with Ubuntu), had no problems. Well being satisfied i jumped back over to my windows hard disk to play some games. Well heres were i started banging my head into the wall ](*,) . I rebooted and started up Ubuntu, only to find out the damn thing doesn't work any more. When Ubuntu is starting up it gets to the part with the scrolling bar. It gets all messy looking and freezes. My system specs are like this 

AMD 64 +3000
2.01 ghz
1.00 gig ram
ATI X1600 GPU

Hope theres a fix, thanks

---

### Post by BoneKracker on 2006-11-29
I don't think anybody is going to be able to help you from the information you are providing.

I think you should describe in more detail what changes you made to the system (when you say you "set it up").  Did you install a different kernel?  If so, that's the kind of change that doesn't take effect until you reboot, which might explain why it was broken when you switched back to Ubuntu.  If you made changes to your Xorg configuration, those don't take effect until you restart X (which might also explain things).

It might also be useful to see you Xorg configuration.  Boot from the cd, mount your hard drive, and copy/paste the following file into a post.
```
/etc/X11/xorg.conf
```

In short, try to provide some specific details.  (What ATI driver, what motherboard or chipset do you have -- I know it's hard to know what details to provide, but information pertaining to your graphics-related hardware or pertaining to graphics-related configuration choices you made will help people figure out what's fishy. :)

---

