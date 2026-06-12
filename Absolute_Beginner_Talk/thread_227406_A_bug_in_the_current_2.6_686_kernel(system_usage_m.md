---
title: "A bug in the current 2.6 686 kernel?(system usage maxes out)"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by underwater on 2006-08-01
I ended the title with a question mark because I"m not sure if it is the kernel, a module loaded by the kernel, or etc, but it only happens when my laptop is running the 686 kernel

Basically,  the machine is extremely slow when using the 686 kernel.  CPU usage is listed at 99% most of the time but no program is listed as using that much cpu power.  If I flip back to the 386 kernel, everything is fine.  

I guess I'm kinda curious how a newbie goes about diagnosing this, and then if it is something that hasn't already been reported reporting it, or possibly in the extreme case, patching it?

Is there a way I can look at what modules are using what cpu and maybe find something that way?  What's my next step?  in general what is the next step in this sort of situation?

---

### Post by ape on 2006-08-01
try running this command as root:

echo 1 > /sys/module/processor/parameters/max_cstate

If it works to make the processor utilization go down, add it to your /etc/rc.local file to get run on every bootup.

---

