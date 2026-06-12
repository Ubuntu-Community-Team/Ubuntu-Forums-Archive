---
title: "Trimming boot times"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by qpwoeiruty on 2007-02-16
On my machine (AthlonXP 2700+, 1980MHz @ 1.45V, 1 GB DDR400 RAM), Ubuntu takes quite a bit of time to start up. I've spent the last couple days cleaning up things the best I could.

Original boot was 1:27 and current is 43s-44s.

Tweaks I've done: concurrency on, profile (6s), static ip (38s), (+4s added to boot for some reason in between), removed unnecessary services (4s).

I was wondering how I could, if possible, speed up the boot time even more.  I was thinking of perhaps removing usplash and was also hoping to reduce the "sleep 1" from portmap to something smaller like 0.2. Is there a safe lower limit to the sleep time for portmap or anyway to load it earlier, remove the sleep 1, and load the dependants of portmap later on so that I don't have that lag?

What about setting the hardware clock? Is that possible to just do it on shutdown instead or is it required for proper startup?
Or moving the files that readahead loads onto one contiguous portion of the disk and reprofiling? (I'm hoping that it would increase disk throughput, making readahead take less time to actually read it).
Any suggestions or something else I'm missing?

Thanks for looking
[Current bootchart](http://img181.imageshack.us/img181/9221/currql4.png)

---

### Post by sardion on 2007-02-16
This is way past what I would call absolute beginner talk, but ...

you can try removing the sleep 1 from portmap.  it may break things.  it may break them only sometimes even.  but i have removed it and its fine.

disabling usplash will gain you some time for sure.

reprofiling so readahead can get betetr thruput is of course the best thing you can do.

but i have to ask... why do you care so much about boot speed?  if its desktop machine why not leave it on all the time?  if its a laptop why not just suspend?

---

### Post by cam_tram on 2007-02-16
Try a slimmed down custom kernel, removing extraneous modules and drivers may be able to cut down your boot time.

---

### Post by sardion on 2007-02-16
Second that.

A custom kernel (ideally with everything needed compiled in, no modules at all) is the fastets.

---

### Post by qpwoeiruty on 2007-02-16
> **sardion said:**
> This is way past what I would call absolute beginner talk, but ...

you can try removing the sleep 1 from portmap.  it may break things.  it may break them only sometimes even.  but i have removed it and its fine.

disabling usplash will gain you some time for sure.

reprofiling so readahead can get betetr thruput is of course the best thing you can do.

but i have to ask... why do you care so much about boot speed?  if its desktop machine why not leave it on all the time?  if its a laptop why not just suspend?

Sorry, I installed Ubuntu about 2 weeks ago and have only started using it in earnest for a week or so. I'm not really sure what qualifies as a "beginner question" or not yet.

Even though I've reprofiled once, it hasn't really had an effect on throughput. Readahead has almost no throughput according to bootchart for the first 5s or so and the rest (~7s) is less than 50% max. Actually, readahead is taking ~10s to load now where it took ~5s when I started.

As for why, I shut down the computer several times a day. Heat, noise, and light are the primary reasons... If I need to get something printed or copied down, I'd like to have the system up as quickly as possible when I need it.

[QUOTE=cam_tram]Try a slimmed down custom kernel, removing extraneous modules and drivers may be able to cut down your boot time.[/QUOTE]

I've heard about doing that before and I did a quick google search on that but I can't find anything really helpful. Is there a place to go where I can learn more about making a custom kernel and figuring out what I need and what I don't?  How significant of an improvement should I expect if I use a custom kernel?

Thanks for the very quick replies!

---

