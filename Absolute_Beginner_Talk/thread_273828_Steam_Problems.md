---
title: "Steam Problems"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by blindmelon7 on 2006-10-08
I just installed my first linux os (Dapper AMD64) yesterday on my brothers computer and so far I have found it to be  much better than windows (I'm seriosly considering converting MY computer).

I sucessfully installed Steam (or so I thought) using Wine and I had it running for a few hours, at this point it opened and closed fine using both the terminal and the desktop shortcut. While attempting to resolve my resolution problem (which everyone seems to have) I had to log back in several times. The next time I clicked on the steam shortcut the "updating steam" window popped up then dissapeared. I tried to open it in the terminal and this happened:

tommy@tommy-desktop:~/c/Valve/Steam$ wine steam.exe
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x60dd4fc0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0016, blocked by 0009, retrying (60 sec)

Can anyone help me?

---

### Post by mysticrider92 on 2006-10-08
I am not quite sure what the best solution here is, but I would recommend re-installing OpenGL or X11 (I guess). I am a bit new to Linux, but that is my best guess. Running things in Wine can be very tricky, and it doesn't like some programs.

I don't know if that will help or not, but I hope it does.

---

### Post by blindmelon7 on 2006-10-08
Thanks for replying! My computer just crashed and when I turned it on again it was working! Very strange... I think it might be something to do with all the fiddling I've been doing trying to get my screen the right size :-k, I must have tried about 10 different tutorials, each one changing SOMETHING. *sigh*

---

### Post by blindmelon7 on 2006-10-08
Heh! This is confusing!!!!!!! Its doing it again!

---

### Post by fragos on 2006-10-08
HOWTO's are useful but use them with caution and only after you understand what each step is doing.  A HOWTO that worked for one might not work for another because it may be dependant on a different version of your distrobution or there may be subtle differences in hardware that prevent something from working.  People who write HOWTOs do so with a desire to help but the effectiveness of their HOWTO may be impacted by a lack of knowledge of other configurations.  The safest solutions are those that are implemented with GUI tools.

---

### Post by NoTiG on 2006-10-09
try this... under section "device" in xorg.conf.... add

```
Option     "NoDCC"
```

ps. make sure you back it up first, and make sure whatever resolution you desire is listed in there somewhere

---

### Post by blindmelon7 on 2006-10-09
Your not going to beleive this; I literaly kicked my computer, restarted and it worked! Its seems pretty stable as well! (I'm talking about both the steam thing AND the resolution problem).

Who says violence doesn't solve everything?

---

### Post by haxer on 2006-10-09
good for you not to good for your computer :)

---

### Post by Aberrix on 2006-10-09
> **blindmelon7 said:**
> Your not going to beleive this; I literaly kicked my computer, restarted and it worked! Its seems pretty stable as well!

"concussive maintenance"

---

### Post by mysticrider92 on 2006-10-09
> **blindmelon7 said:**
> Your not going to beleive this; I literaly kicked my computer, restarted and it worked! Its seems pretty stable as well! (I'm talking about both the steam thing AND the resolution problem).

Who says violence doesn't solve everything?
That is one way to solve things. :D  Just make sure you don't kick it too hard.

---

### Post by fragos on 2006-10-09
On occasion problems will work themselves out after a few reboots.  Too bad that's not all the time.  Violence can has immense psychological value.

---

