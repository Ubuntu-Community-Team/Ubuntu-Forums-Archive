---
title: "Shutdown screen problem"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Jake808 on 2007-04-19
This isn't so much a problem as something weird thats happening at shutdown.  I have Ubuntu 7.04 installed.  When I boot up, the splash screen is normal but when I shut down the splash screen is not in the middle of the screen. It starts about a third of the way across the screen and over laps the right-hand edge and part of it is visible on the left-hand edge of the screen.  Its not affecting the performance of Ubuntu but its just annoying. Anyone know how to fix this?


Thanks,

Jake

---

### Post by tbg58 on 2007-04-19
I'm not certain, but it sounds like your video driver may be switching to another resolution as soon as GDM starts to switch off.
Check the type of video card you have -- in my case I have an NVidia card that had something like that until I got the driver installed for it.
This is a non-FOSS driver, but you can get it under Applications, Add/Remove, then type nvidia.
Note that the line above is an example only -- I don't know what kind of video card you have.  NVidia and ATI cards may both exhibit the kind of behavior you describe, but this is a guess on my part.
Hope this helps.  Good luck!

---

### Post by HandsofGod on 2007-09-11
I've faced the same problem, my notebook runs on NVIDIA GeForce Go 6150, Ubuntu 7.04 with nvidia driver obtained from "Restricted Device Manager". It'd be really appreciated if anybody can give me the solution.

---

