---
title: "Graphics card help! Urgent!!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2007-10-20
I got my new graphics card today and installed it and got this after installing the drivers after trying to activate visual effects. So I'm lazy and am gonna go with a reinstall, what should I do to set up the graphics card and visual effects once I get it working again? (NVidia GeForce 5200)
Ok, I got it working (maybe) but on reboot it has been running local boot scripts for a while....... any help?   
Image


[img]http://myskitch.com/spyker3292/p1010005-20071020-141108.jpg[/img]

---

### Post by Can+~ on 2007-10-20
First: What's the name of the new graphics card?
Second: Can you get to the bulletproof? Or at least a console? (Ctrl+Alt+F1 (to F6))

---

### Post by spyker3292 on 2007-10-20
> **Can+~ said:**
> First: What's the name of the new graphics card?
Second: Can you get to the bulletproof? Or at least a console? (Ctrl+Alt+F1 (to F6))

Oh ya I forgot that :).

It's an Nvidia Geforce 5200. Let me check about the console.

---

### Post by spyker3292 on 2007-10-20
Well I obviously screwed quite a lot of stuff up... on boot I got a fsck fail... I guess I'll just go with a reinstall, do you have an answer for my question about installinjg the drivers correctly?

---

### Post by Ant_Merlin on 2007-10-20
Hi that looks more like refresh rate problem rather than Driver, do you have a CRT as monitor? if so best way in Gutsy is to go to system> administration>screens and graphics, select monitor, refresh rate, resolution and the driver and reboot.

If you havent reinstalled yet you can use terminal. sudo nano /etc/X11/xorg.conf

Change resolutions supported and refresh rates and then save and reboot.

---

### Post by tseliot on 2007-10-20
> **spyker3292 said:**
> Well I obviously screwed quite a lot of stuff up... on boot I got a fsck fail... I guess I'll just go with a reinstall, do you have an answer for my question about installinjg the drivers correctly?

Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "nv" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vesa", "vga" or "fbdev" instead of "nv" and try again.

---

### Post by spyker3292 on 2007-10-20
> **Ant_Merlin said:**
> Hi that looks more like refresh rate problem rather than Driver, do you have a CRT and what version of Ubuntu are you running?

It's LCD and just started after installing drivers, works fine on XP. I'm just reinstalling :). How should I correctly set up my card? 
(In reply to above post)- I have to go, I'll try that later before just reinstalling.

---

### Post by spyker3292 on 2007-10-20
Ok, I did the dpkg-reconfigure xserver-xorg and now it's rebooting, it just seems to be taking a while on Running Local Boot Scripts...

---

### Post by Hopworks on 2007-10-20
I had that happen to me too, except the result was a little different. I forgot to put in HorizSync and VertRefresh values in for my Dell E207WFP. I'm not sure if that was the cause, but I googled it, got the values, put them in, and it works fine.

---

### Post by spyker3292 on 2007-10-20
Now I'm a little concerned... it's been running local boot scripts for 5-10 minutes...

---

### Post by spyker3292 on 2007-10-20
Ok... really concerned... HELP!

---

