---
title: "Lock screen trouble."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-12-25
Hi

Once my laptop remains inactive for some time the screen locks. if I immediately return back with password it works fine.

But if I keep it idle for sometime the enter password dialog doesnot appear. Instead a cursor blinks. and "Linu" is written in yellow next to it.

---

### Post by Rocket2DMn on 2007-12-25
Sounds like your screensaver might be crashing the X server.  You could disable the screensaver and see what happens - if that fixes your problem, then we know the cause!  You can either leave it that way or try other screensavers until you find one that works.
Does the laptop try to go into standby at all?

---

### Post by Guruprasad on 2007-12-25
Hi

Thanks for the reply.

I dont think its problem with screensaver.

i already tried keeping the screensaver off.  Also kept the screensaver idle time as 1min and checked. Sceensaver worke fine. I was able to log back.

---

### Post by Rocket2DMn on 2007-12-25
So then is the computer going into standby?  This tends to cause problems for some people, too.  Also when that happens, try CTRL+ALT+BACKSPACE and see if X restarts.  If it does, then the computer isn't locked up, but X is broken.  If THAT turns out to be the case, we can try reconfiguring X.

---

### Post by Guruprasad on 2007-12-26
I disabled the sleep option. Now it doesnot create problem. Can you tell me how to reconfigure x?

---

### Post by Rocket2DMn on 2007-12-26
You don't need to reconfigure X - it seems that your computer going to sleep is the source of the problem.  You could just let it go and not put your computer to sleep (this still uses battery anyway, just less than normal).  I use the hibernate feature a lot.
However, if you want to try and be able to use the sleep mode, you can google around or just search the forums with your laptop model or brand and see if others have had the problem and been able to fix it.
Otherwise, please post some computer specs like your model/make and your video card and I'll see what I can do.

---

### Post by erginemr on 2007-12-27
> **Guruprasad said:**
> Hi

Once my laptop remains inactive for some time the screen locks. if I immediately return back with password it works fine.

But if I keep it idle for sometime the enter password dialog doesnot appear. Instead a cursor blinks. and "Linu" is written in yellow next to it.

Please read the following post and check out the links I have given in my post there:

[http://ubuntuforums.org/showthread.php?t=608426](http://ubuntuforums.org/showthread.php?t=608426)

---

