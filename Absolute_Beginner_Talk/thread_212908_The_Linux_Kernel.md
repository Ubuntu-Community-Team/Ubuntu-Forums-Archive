---
title: "The Linux Kernel"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by siccness on 2006-07-10
Hey, I've recently tried to learn a little bit more about Linux, rather than just using it. So I decided to have an understanding of the Linux Kernel, and how it works, but unfortunately, I can't quite understand the difference of certain features when being a module, or built-in. A number of how-to guides state that a particular feature MUST be enabled as a module, rather than built-in and vice-versa. Why is this? 

I've tried playing around, compiling the kernel numerous amounts of times to see, and you bet - for ALSA theres a particular option that must be built-in, rather than set as a module. One worked, one didn't but I can't find out why?

Anyone know what difference it makes, and why?

---

### Post by brentoboy on 2006-07-10
I'm not entirely sure that this is "absolute beginner talk" and I am not sure if my response is too basic, or right in line with what you are asking about...

modules are compiled as little binary chunks of execuable code that are not part of the main kernel binary.  they are advantageous because if the kernel is smaller, it can fit in less memory and is (arguably) faster.

on the other hand, becuase the modules have to be loaded into the kernel in order to be useful, they make booting slower at boottime (the time it takes to load them into an already running kernel) and slower when being executed becuase they arent linked right inside the main kernel.

It would be silly to compile the entire kernel with built-in support for everything under the sun.  So liveCDs have all the modules included, but only compile built in support for things most people need.  Then, they detect what is needed and load those modules.

Why some modules are required to be built in, and others work as modules is beyond me, and I am sure the reasons are specific to each feature.

good luck.  I personally would spend more time learning about the conf files for major linux daemons like apache and samba before I would give too much time to studying the kernel.  but, that's me.

---

### Post by siccness on 2006-07-10
Thanks for your reply, much appreciated.

You're right though, I'm not sure if this thread belongs under this section either. Perhaps a moderator could move it to the correct section, as I couldn't really find a suitable area for it. Sorry!

---

