---
title: "Unknown Disk IO"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-16
Ok, this probably sounds really stupid thing to ask, but I'll do it anyways :p

With my new conky script, I know exactly how the disk is being used (amongst other things) and I noticed something: every 2 or 3 seconds, something is writing between ~50 and 250 KiB to disk!  This is with no apps running, system tray empty, etc etc. - I am not afraid of any malware, I am assuming this is completely normal, but it just seems odd...

I can understand it *reading* every couple seconds maybe, but why writing?  I guess I just want to know what's doing it and why... :rolleyes:

---

### Post by FuturePilot on 2008-01-16
I'm not sure if this is the issue, but it could certainly be one explanation of it. The system updates the EXT3 journal about every 5 seconds. What you are seeing could simply be the journal being updated.

---

### Post by ryanVickers on 2008-01-16
oh ok then... I knew that but never would have guessed it... :p

You would think that if nothing changed, there's nothing to do, but I guess I won't complain, it's done a fine job so far! :p ... lol when I really think what it's survived... 2 motherboard failures, countless hard powers off, a couple power outages, etc. etc.  :D  where as windows... well... lets just say this is along the lines of the whole reason I switched to Linux (but not the only reason why I stayed ;))

---

### Post by FuturePilot on 2008-01-16
Yeah, I've noticed the same type of activity through Conky when my computer is idle. I guess there's always some thing to write.

---

