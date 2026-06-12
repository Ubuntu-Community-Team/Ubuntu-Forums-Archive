---
title: "4 monitors in ubuntu"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by seantheman on 2007-08-07
Hey, I recently got a new motherboard with two pci-e x16 slots, and I have plugged into them two video cards, an e-geforce 7600gt, and an en-7300gt.  I have 4 monitors all hooked up to them, and all is well with windows xp.  However, my question is: will I be able to hook up all of them with ubuntu?  I am running compiz fusion right now, (I don't mind changing to beryl or somthing if fusion isn't compatible) and what would be awesome would be if I could get the 3D desktop cube working, stretched out on all 4 monitors.  I know this works with 2 monitors, but what about 4?  Right now, I don't even know how to get all the monitors working in ubuntu, even without the desktop effects.  Would love to get this working...

---

### Post by dfreer on 2007-08-07
if those are nvidia chipsets, i don't see a problem with getting it working. go ahead and give it a try, check out *sudo nvidia-settings* to get them configured. Let us know if you have any specific problems!

---

### Post by seantheman on 2007-08-07
Everything seems to work, (even if it's a little slow), except, now I don't have any window borders!   someone help!  I tried restarting, but to no avail!

---

### Post by seantheman on 2007-08-07
Ok, it seems that whenever I try to enable any more but one monitor at a time, my window borders disapear!  All the other desktop effects seem to be working, except this!  Would really like some help... I'm so close!

---

### Post by aldenhg on 2007-08-07
If you have your session set up so that Compiz is starting by default, you can always remove the entry in your Sessions dialog box or you can hit Alt-F2 and type in metacity --replace. That will load up the default window manager and you'll have your window decorations back. As for the problem itself, I'm muddling through that one myself at the moment and I'll post something here when I get it fixed. I don't think that the root of our two problems is the same, but you never know with alpha software.

---

### Post by seantheman on 2007-08-07
Ok, thanks.  Much obliged :) 

Hope to get a solution for this too!  I'll try experimenting with beryl, see if I get better results.

---

### Post by seantheman on 2007-08-07
Great news!  Seems beryl works fine!  Too bad about compiz fusion though...

---

### Post by seantheman on 2007-08-07
Scratch that:  It works fine... in only one monitor.  the other monitor still has the same problem

---

### Post by aldenhg on 2007-08-07
One thing you might want to keep in mind is that Compiz and Beryl are both VERY CPU intensive, so running them on 4 monitors might make for a pretty sluggish experience no matter what you do. If I were you, I'd hold off on running it full time until the project matures a little more.

---

### Post by dfreer on 2007-08-07
i would think you would have better multi-screen support in compiz fusion then beryl, but idk.
As for window borders, try adding this line to your /etc/X11/xorg.conf (make sure to back it up first!):
```

Section "Screen"
.....
    **Option         "AddARGBGLXVisuals" "True"**
.....
EndSection

```

As for multiple monitors, I'm not sure whether you would need to add this line to all 4 sections, or just one. I guess you can experiment and try?

---

### Post by Kitsun on 2007-08-07
If you do manage to get it working I recommend posting a video to youtube.

Helps gives Ubuntu some well-deserved hype.

---

### Post by aldenhg on 2007-08-07
I think I've got it. Go through all the Screen sections in your xorg.conf file and change DefaultDepth to 24 if it isn't already. The AddARGblahblahvisuals option should be put in your device section along with your driver. If the defaultdepth for every screen is already at 24 this won't help.

---

### Post by seantheman on 2007-08-07
I just tried doing that, and experimented but to no avail.  On compiz fusion, still no change: no borders.  On beryl, the same: Borders on one windows, none on the other.  Really confusing...

---

### Post by seantheman on 2007-08-07
Ya, all my defaultdepths are already 24.  Still no luck with experimenting.  (Although, with just 2 screens, twinview has no problems with borders and such.  not what I'm looking for though.)

---

### Post by darksong on 2007-08-07
I was going to try this on My PC but i realised that my graphic card would not handle it very well (even though its pretty good) The graphics has to be able to make a picture on 4 screens instead of the 1 meaning it has to split its reacourses up into 4. It you SLIed 2 7600gt's you could run it with much better results. (With my 7600gt that would give me (standard sli) 1000mhz core + 512mb DDR3 of graphical powa)

---

