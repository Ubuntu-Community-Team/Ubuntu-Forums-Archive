---
title: "Dual Core"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-07-06
Hey there, I just dropped in an AMD Opteron 164 Socket 939 64 bit Dual Core Processor. I originally had been running an AMD 3000+ 64 bit, is there anything I need to do or drivers to download to make sure I'm getting full work out of both cores and that it's seeing both cores and not just one? I'm in the midst of a burn in making sure no real hiccups occur but I want to make sure I am taking care of everything. Anyone have any help or ideas? Thanks!

---

### Post by shrift on 2007-07-06
For dual core useage you need an SMP kernel. I believe that that is enabled by default in Feisty. To take full advantage of a 64bit processor you have to use a 64 bit kernel, so you may also need to change to an Ubuntu 64 release, if your not already using one.

---

### Post by shrift on 2007-07-06
An easy way to see if your using both procs is to run "gnome-system-monitor". Under the System tab it lists how many processors it is using.

---

### Post by Tumpster on 2007-07-06
See now I'm having random hard locks and also freezes, can anyone figure why this is? The processor is seated properly and the heatsink is as well. Any ideas?

---

### Post by Tumpster on 2007-07-07
BUMP! I'm getting this when I do that:

craig@craig-desktop:~$ gnome-system-monitor
glibtop: This machine has 1 CPUs, 1 are being monitored.
smooth_refresh is active = 1

I don't seem to see a system's tab at all.

---

### Post by Tumpster on 2007-07-07
Where do I get this smp kernel?

---

### Post by shrift on 2007-07-09
Tumpster, are you still using Dapper like your profile indicates? I think I gave you info based on the assumption you were using Feisty. : ( Sorry if that was incorrect.

---

