---
title: "cpu 100% every 5 seconds or so"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by dragonflyFZX on 2006-12-02
hi,

in gkrellm, i notice that my CPU goes to 100% for a fraction of a second every 5 seconds or so.  This is annoying, cause it keeps my laptops temp high enough to keep the fan going all the time.  It is always on and in the living room so it bothers me.

What process is causing this? It was not always like this, started a few days ago.  I tried to figure out what process it is using top, but since it is only a fraction of a second, i cant figure out which one it is.  Can someone help me on this one?

D

---

### Post by Peepsalot on 2006-12-02
I found that beagle would often max out my processor when it would otherwise be idle.  Then again, I had also foolishly told it to index everything under my root directory...BAD IDEA.

Can you open the System Monitor under System->Administration menu and see which process it is?  Sort the processes in this program by CPU percentage, and see what floats to the top.  You can also check out the total CPU time used by each process.

---

