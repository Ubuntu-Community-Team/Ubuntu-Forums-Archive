---
title: "[SOLVED] i855GM slow scrolling + slow window movement"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Eberhard on 2008-01-29
Hi Guys, First Thread...

I recently converted from WinXP to ubuntu 7.10 on my laptop. I'm having slow scrolling in FF and Opera and slow window movement. It feels like it would feel on XP without any driver installed.  I've of cause searched quite a bit on this issue with out any good results. 

My graphics Card is an integrated 855GM, i have 2Gb ram and a 1.7 GHz pentiumM. I've tried to change from "intel" to "i810" in the xorg.conf file but no change.

I've come under the impression that Ubuntu 7.10 installs the driver automatically so i cant figure why i'm having this issue.

I hope you can help me guys.

UPDATE:
I have found out that Direct Rendering is not enabled. Can the slow scrolling /slow window movement be related to this? It gave me the following after writing glxinfo | grep direct

> direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

How do you enable this?

---

### Post by FuturePilot on 2008-01-29
Are you using Compiz?

---

### Post by Eberhard on 2008-01-29
I think i've had it installed but it did not work very well - I've unchecked the Advanced Desktop effects settings in Applications -> Add/Remove, so it should'nt be installed?

I'm not that interested in having compiz - is there a way to see if it is installed and if so, remove dissable it?

---

### Post by FuturePilot on 2008-01-29
Just go System>Preferences>Appearance. Go to the Visual Effects tab and make sure the None option is selected.

---

### Post by Eberhard on 2008-01-29
The "None" option is allready selected. Can it be that my system is working as it should and that the slow scrolling / window movement is just because that linux/ubuntu isnt as good at using the hardware as windows is?

---

### Post by FuturePilot on 2008-01-29
No, I think that you may need the i810 driver. Intel cards have great Linux support. Though I'm no expert with Intel cards so I wouldn't really know how to set it up. Hopefully someone else might.

---

### Post by Eberhard on 2008-01-29
Ok. As i wrote in the first post, I have tried the i810 with no luck - but maybe some further custemization is necessary.

---

### Post by Eberhard on 2008-01-30
After reinstalling Ubuntu 7.10 everything is fine. glxinfo | grep direct gives me Direct Rendering: Yes... The problem might have been that i have tried installing beryl myself instead of just using the compiz-fusion that comes with Ubuntu.

---

### Post by AlphaBob on 2008-03-24
> **FuturePilot said:**
> Just go System>Preferences>Appearance. Go to the Visual Effects tab and make sure the None option is selected.

Many thanks!  I just moved from 7.10 which was working quite well, to 8.04 today.  My system scroll speed dropped way down.  It even seemed like I was typing faster than the screen could keep up with.

The Visual Effects setting was set to medium (what it was in 7.10.  Putting it to none really pepped things up.

Can't say that I notice a heck of a lot of visual difference.  Probably something subtle.

Thanks again!

---

