---
title: "Screen brightness fix for G5 iMac (maybe more)"
date: 2006-11-17
forum: Apple PPC Users
---

### Post by stream303 on 2006-11-17
Another reason to thank the users on this forum!

My Rev-A G5 iMac was pretty bright with Edgy, and for me this partial solution was revealed from the G3 guys:

[http://www.ubuntuforums.org/showthread.php?t=299694](http://www.ubuntuforums.org/showthread.php?t=299694)

While it isn't a true brightness control, I can bring my "apparent brightness" down a bit and make waiting for a keyboard brightness control a little bit easier:

In a terminal:

**xgamma -gamma 0.8**

That's it!  I run anywhere from 0.7 to 1.0 (default) depending on my needs - usually under 1.0 most of the time.

I probably wouldn't edit mission critical photos until I can really calibrate the gamma, but for now this helps take that edge off.

Thanks again gang!

---

### Post by Torrance on 2006-11-17
Really? I have an iMac G5 (rev a) and I'm convinced its actually slightly darker than Mac OS X... though I can't verify that. I tried pushing the gamma up beyond 1.0 a while back but it just washed out the screen.

---

### Post by stream303 on 2006-11-18
You got my wheels spinning - wish I had more hardware knowledge.

I wonder if the brightness setting is stored in openfirmware somewhere?  I'm no longer dual-boot and I'm wondering if you change your brightness in OSX (strangely enough under the accessability preferences and not the display preferences) would it stay the same when you boot Ubuntu?

Unfortunately, when I did a dedicated install I also reset the pmu/smu.  Now my screen is as smokin' bright as when I first installed OSX.

I may be way off base here since I don't have great apple hardware knowledge, but man if you are dual-boot could you try this?

---

### Post by Torrance on 2006-12-08
My OSX brightness is always set as bright as it can go and that's had no effect.

Ben H (the ppc linux guy) from the Debian PPC list said it was quite likely the iMac screen is dimmer than it is in Mac OS X as they've kinda guessed a safe brightness value for all the iMacs running Debian/Ubuntu (and all Linux?). Unfortunately, I haven't found a way to fix this yet.

---

### Post by stream303 on 2006-12-09
Aside from the xgamma gimmick, In my case the screen is just a tad bright so I am using dark backgrounds.

I'd almost be perfectly satisfied if I could find a way to change the bright-white background of these Ubuntu forums into something a little less harsh.  I've tried custom firefox color settings, but it tends to degrade the graphics on the forums.

Too bad the forums aren't lynx-friendly - well, they do work, it's just that they are so busy it's kind of a pain.

---

