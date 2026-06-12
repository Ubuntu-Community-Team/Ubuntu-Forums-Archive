---
title: "GRUB Menu error?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by andrewlinn957 on 2007-03-06
On startup the GRUP boot menu displays Ubuntu(generic) and Ubuntu(recovery) twice, like

Ubuntu Generic
Ubuntu Recovery
Ubuntu Generic
Ubuntu Recovery
win xp

why is this, and can i stop this, because im trying to make XP the default os and im not sure why there are 2 ubuntus even thought i have only 1 installed. thanks

---

### Post by confused57 on 2007-03-06
> **andrewlinn957 said:**
> On startup the GRUP boot menu displays Ubuntu(generic) and Ubuntu(recovery) twice, like

Ubuntu Generic
Ubuntu Recovery
Ubuntu Generic
Ubuntu Recovery
win xp

why is this, and can i stop this, because im trying to make XP the default os and im not sure why there are 2 ubuntus even thought i have only 1 installed. thanks
You had a kernel update, which is the top 2 Ubuntu entries...the bottom 2 Ubuntu entries are the kernel that was installed originally.  You have just one Ubuntu, but a new kernel and the original kernel that you can boot to.  I'd recommend leaving them both for now, in case you have problems booting the newer kernel.  If there's another kernel update & you have 3 different kernels, then you can probably go into Synaptic & unstall the oldest one.

---

