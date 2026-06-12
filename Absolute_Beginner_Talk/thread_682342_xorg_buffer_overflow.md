---
title: "xorg buffer overflow?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by jaytek13 on 2008-01-29
Okay, so recently I've been experiencing some problems that seem to be related to X. Randomly, X will basically stop functioning, my CPU usage will jump from 5% to 100%, and top reports that xorg's cpu usage is continually climbing. I've let it go for 5 minutes to see how high x's cpu usage would go and thus far it's gone to 47% without stopping, at which point I would ctl-alt-backspace and it would resolve the problem.

Anyways, is there a way I can pinpoint exactly what is causing this? I guess this sounds like more of a memory leak than a buffer overflow.

---

### Post by Shazaam on 2008-01-29
Are you running Firefox also when this happens?

---

### Post by jaytek13 on 2008-01-29
> **Shazaam said:**
> Are you running Firefox also when this happens?

Firefox has been running when this has happened. In fact, the most recent time it happened  it occurred right after I tried to open firefox. I am using the most recent version of ff, though.

Oh, I edited the post to add "it sounds like more of a memory leak" but in fact that is incorrect also. My memory usage stays the same, it is strictly the cpu usage that jumps to 100% and won't go down.

---

### Post by Shazaam on 2008-01-30
I have the same problem with Firefox in Gutsy. What I have done to temporarily work around this was to install Firefox3.0 alpha from the Gutsy repo's. Unfortunately this version (Grand Paradiso) introduces other bugs but it DOES tone down the Firefox lockups.
Version 2 has almost constant memory problems and the cpu bug.
Version 3.0 alpha only spikes intermittently and drops the memory usage quite a bit.
As  this version is at ALPHA use it at your own risk.

---

