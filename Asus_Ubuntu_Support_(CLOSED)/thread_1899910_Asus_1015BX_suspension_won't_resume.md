---
title: "Asus 1015BX suspension won't resume"
date: 2011-12-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by PippoPalmieri on 2011-12-24
Hi guys, 
I'm new to linux and i really need some help because i'm out of ideas.
The problem is that my netbook (asus1015bx) won't resume from suspension. i tried every fix i could find on the internet but to no avail, i also tried to disable c60 from the bios, nothing changed.
When i close the lid or hit the suspension button the netbook does his job and suspends, but then when it has to resume you can see the hard disk led working for a bit and then stopping, while no backlight comes up on the screen. The only way to restore everything is to unplug the power cable or the battery and reboot. 
I'm using ati proprietary drivers (11.12)
I would be so thankful if someone could troubleshoot me through this step by step, i'm a newbie and i'm still getting used to this.
Thank you!
edit: i found out hibernation doesnt work either! when it has to resume, the backlight goes on but nothing appears on the screen and rebooting is the only way to fix it. Please help meeee thank you!


edit2: i'm running oneiric ocelot, i just formatted and without updating anything it works fine. My thought is: could it be an ati driver problem? It seems like a plausible solution, im going to update everything but those and see if it still works. Those drivers do not make my experience any better even if i have a decent video card, a 6290 Radeon with a c-60.

edit3: everything is working perfectly now, may i ask you, is the difference between fglrx and open source drivers so big to justify the loss of hibernation and suspension? I dont think it's worth to install the fglrx, they were installed properly, but i couldnt really notice a difference...
Or if this is a known issue, is there a way to install the fglrx and have a workaround for this problem?

---

### Post by Barfication on 2011-12-30
Well, problem already solved!

I have a similar problem, only with a nVidia laptop.

I have had the problem since Ubuntu 11.04. I guess it has something to do with how Unity, Xorg and the graphics driver are working together. Because the open drivers are open it is easier to get everything working properly with those drivers instead of having to guess how the closed driver works. (I'm not an expert so it's just me guessing.) I hope the issues will be fixed in 12.04.

A workaround would be just preventing the laptop to hibernate. You can adjust your settings that the laptop just shuts down when you close the lid.

You could also try another distro. I've only found this problem in Ubuntu (since Unity). 

But if I were you I would just stick with the open drivers. If you don't notice any difference in performance, why change?

---

### Post by Barfication on 2011-12-30
I have found another workaround. (That works on my laptop, maybe not on yours.)

You can log off as a user. But when you log in again choose "Ubuntu 2D". (You can do this by clicking on the wheel.) 

Then you'll get Unity 2D. Unity 2D is a lighter version of the Unity desktop. I don't seem to have the problem with Unity 2D.

---

### Post by 2F4U on 2011-12-30
On one of my laptops, which also has an ATI card but uses the open source drivers, suspend/hibernate/resume only works, if I add nomodeset to the grub kernel parameters.

---

### Post by zylx on 2012-07-05
I also have Asus 1015bx but with c-50 APU. And, I laso have problem with suspension and hibernation. Netbook goes sleep, but (on fglrx) when it has to resume, display stays black and nothing apear. On open source drivers the displays turn on for a second, but later turn off and i have to shutdown netbook (long pressing power button). Any idea?

---

### Post by Toriam on 2012-07-10
50 Posts! Ignore this guys...

---

### Post by lolwhites on 2012-07-24
Removing the proprietary driver worked for me.

---

