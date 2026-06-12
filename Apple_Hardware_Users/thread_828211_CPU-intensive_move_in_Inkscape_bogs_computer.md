---
title: "CPU-intensive move in Inkscape bogs computer"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by gphaze on 2008-06-13
I experimented with "Fractalize" in inkscape yesterday. nice feature..worked well.

But afterward, after all the processing was over and done with, the computer seemed very sluggish, as though it was still clogged up with who-knows-what as a result of having done a very computationally-intensive procedure.

Restarting cleared things back up, but I'd like to know if there's a better way I can handle that in the future...

I view Linux, like OS X, to be robust in its ability to handle big chores, then to keep on going. The experience I have on OS X after a CPU-intensive operation is that speed and responsiveness return fairly quickly, and I would *like* to experience that on the linux install too.

Any suggestions?

gphz

---

### Post by stream303 on 2008-06-14
To keep an eye on the processes, you can run *top* in a terminal while you are doing your inkscape stuff.  After shutting down inkscape, look at top again and see what may be hanging.

My favorite alternative to top is actually **htop** which I find indispensable - much more relevant info is displayed if you don't have much experience with deciphering top's output.  Htop is one of the very first things I download from the repos...

With HTOP, hit F6 for a nice sort order of different values like cpu, memory, or time...

---

