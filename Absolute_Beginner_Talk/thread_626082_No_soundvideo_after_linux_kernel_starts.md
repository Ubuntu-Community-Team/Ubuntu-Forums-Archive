---
title: "No sound/video after linux kernel starts"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Aranthos on 2007-11-28
Ok, I've had a bit of a snoop about and I've found a few threads from people who have no video when booting, but none of them seem to have the same problem as me.

Every time I try to boot Ubuntu, be it from a Live CD, or from my HDD, two lines of text appear at the bottom left of my screen, the top one saying "Kernel alive" and the second one saying "Kernel directly mapping tables up to 1000000 [or some such] @ 8000 6000".  I can't guarantee how accurate either of those lines are, as I'm working on what I remember seeing for less than a second before the screen goes dead.

Further, at this black screen, my HDD (this is when booting from HDD - from Live CD there is nothing at all) will crunch away for a few seconds, as if it is accessing data, but nothing actually happens.  I have no sound playing, but I don't have audio in Windoze either, so it might be a hardware issue.

Is it possible that I'm only seeing a small portion of the screen at this point, since during setup I hit Enter instead of Space (due to me confusing the controls) and left all of the resolution options enabled, when my monitor can only display a meagre 1024x768?  Phew...  Long sentence...

Thanks for reading, and bigger thanks if you can help me clear this up  =]

One other thing - Numlock, caps lock and scroll lock are all unresponsive.  Crash?

---

### Post by Aranthos on 2007-11-28
Well, I gotz to go to bed for the night.  Hopefully I'll have a reply by morning.  Thanks for reading folks =]

---

### Post by Aranthos on 2007-11-29
Sorry for the triple post, but I've found out what the problem is.  One of my mates at college (who happens to use Ubuntu on a GeForce 8 card, same as me) has told me it's a driver issue.  I've found and downloaded the Linux drivers for my video card from nVidia, but I don't know how to install them.

[oops]By the way, I have also read about trying the safe graphics mode.  I don't know why I hadn't thought of this already, but I'll give it a shot and report back with the results.[/oops]

Having looked at the boot options screen, there isn't an option to boot a safe graphics version.  My motherboard hasn't got any integrated graphics for me to fall back onto either, which makes things doubly awkward.  I've seen some posts by higher-beings than myself saying that I should enter certain commands into somewhere, though I have no idea where nor how to access this command-prompt thing.  Do I need to use recovery mode?

---

