---
title: "Touchpad driver breaking, 12.04, MB Pro 8,1"
date: 2012-04-30
forum: Apple Hardware Users
---

### Post by Samushighwind on 2012-04-30
I've been using several versions of Ubuntu on my MacBook Pro 8,1.  In the past (and now), I've had problems with the touchpad driver occasionally breaking when I open up my computer after suspension.  

But now that I've upgraded to 12.04, it literally happens every time.  It can be remedied by logging out and logging back in, and thanks to HUD, this is now easy even with no mouse, but it's still annoying and shouldn't be happening.  Any ideas?

---

### Post by Samushighwind on 2012-04-30
apparently whenever it breaks, it thinks every touch is two-finger scrolling.  this explains why all touchpad functions except pointer navigation seem to be preserved.

---

### Post by Kallun on 2012-05-01
> **Samushighwind said:**
> I've been using several versions of Ubuntu on my MacBook Pro 8,1.  In the past (and now), I've had problems with the touchpad driver occasionally breaking when I open up my computer after suspension.  

But now that I've upgraded to 12.04, it literally happens every time.  It can be remedied by logging out and logging back in, and thanks to HUD, this is now easy even with no mouse, but it's still annoying and shouldn't be happening.  Any ideas?

Hi Samushighwind,

If you take a look at [my thread](http://ubuntuforums.org/showthread.php?t=1952532), I was experiencing a similar issue on my MacBook Air. I wrote a little bash script called by pmutils when waking from suspend that just reloads the touchpad module.

I'm not sure if your MacBook Pro will be using the same driver, but you could try using lsmod and pipe it into grep to take a look:

```
lsmod | grep bcm5974 
```

If nothing comes up, running lsmod on it's own will show you a list of loaded modules, so you might be able to work it out from there, then you can just edit my script accordingly :)

---

### Post by Samushighwind on 2012-05-02
MacBook Air drivers and Pro drivers seem to be interchangeable, but at the moment, using HUD to log out and log back in suits me just fine.  I'm looking for a permanent fix.

But thanks

---

