---
title: "External drive won't mount if too cold"
date: 2011-08-14
forum: Any Other OS
---

### Post by qyot27 on 2011-08-14
Exactly what the title says.  I have a couple of hard drives I've put in USB enclosures, and for a rather long while I could just turn the drive on and Windows would find and mount the device without any issues.

For the last year or two, though (IIRC, anyway), one of the drives has had trouble being found and mounted if the temperature of the enclosure is too low.  The drive in question is a 30GB 5400rpm drive (and it's also this computer's original main drive; I swapped it out for a 160GB 7200rpm drive several years ago), which I could imagine might have something to do with it, but the stranger part is that in the event I turn the drive on and it is too cold, it's not that it simply doesn't mount - it drags Windows' performance way down, too.  Music will slow way down, the mouse will move in snapshots when moved, and everything else lags horribly.

After a bit of the drive warming up, this lag goes away, but it still doesn't mount (usually).  If I turn the drive off and then back on again, though, it will mount.  To avoid this, I tend to disconnect the USB cable from the drive, turn it on to let it warm up, then shut it off, plug the cable back in and turn it on again.  Recently, I've even been noticing this behavior starting to occur with the other drive, which is both several years newer and 7200rpm (80GB, if that matters).


Suffice it to say this doesn't happen at all under Ubuntu.  If I turn it on cold, Ubuntu finds, mounts, and can access it just fine.

Does this sound like a driver issue, or just Windows being...itself?  Also, this is XP, not Vista or Win7.

---

### Post by NightwishFan on 2011-08-14
My first thought was a hardware issue but as you have stated the drive functions fine in another operating system, I would have to say it is a driver issue. It is not natural for the system to lag just from trying to plug in a device. I would say that perhaps Windows is trying to mount the device but failing for no obvious reason?

As for ways you can fix this... Perhaps check in the windows monitor if there is a process using up 100% cpu when you try to mount it. Then perhaps find a way to reinstall drivers.

---

### Post by qyot27 on 2011-08-14
Just checked it.

'System' normally uses 2-4% CPU.  I turn the drive on when cold, it skyrockets up to 94-97%.  Unfortunately, I don't know how to get any further analysis on that, because memory usage doesn't seem to change (reported at ~237MB with the drive on or not).  Neither the Windows Task Manager nor Process Explorer XP could show a clear reason for the spike in CPU usage.

Not really knowing anything about the way drive mounting is handled here, any time a drive is plugged in/powered on/etc, there's a small audio hiccup due to the sound used when the drive mounts, and I'd guess that coincides with increased 'System' activity.  With a warm drive or flash drive, this is very momentary.  Less than a second.  With the cold drive, though, it seems to be getting stuck in this step and dragging the CPU usage out for some reason.  At least, until it warms up.

---

### Post by NightwishFan on 2011-08-14
> **qyot27 said:**
> 
'System' normally uses 2-4% CPU.  I turn the drive on when cold, it skyrockets up to 94-97%.  Unfortunately, I don't know how to get any further analysis on that, because memory usage doesn't seem to change (reported at ~237MB with the drive on or not).  Neither the Windows Task Manager nor Process Explorer XP could show a clear reason for the spike in CPU usage.
I know next than nothing about Windows (so I welcome folks that do to chime in here) though I assume that would be because the process using up the CPU is something in kernel mode or some driver process. I know Windows has logging or monitoring tools but as I said I can offer little advise how to peruse them correctly.

As for the whole 'warm' factor that is very interesting.

Well.. though I doubt this is the case if you do not have much data on there perhaps back it up and reformat the drive using Windows to do so. Or does the Windows disk utility not even detect it?

---

