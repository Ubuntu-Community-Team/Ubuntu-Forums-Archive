---
title: "remove unused kernel modules"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by skippy81 on 2006-05-18
I'm bored and want to mess with my system.  I've noticed I have a lot of modules loaded for things like bluetooth and pmcia which my PC doesnt actually have.  Is there a config file which loads them?  I don't really understand how these modules were chosen to be loaded in the first place.  Any tips about how to go about pruning them would be great.

---

### Post by xtacocorex on 2006-05-18
You can use rmmod to remove modules. I don't know how to remove a module for good, but at least it's a start to the learning process.

Some modules are loaded automatically based upon how the kernel was compiled. Others are listed in /etc/modules.

You need to be sudo to run rmmod.

---

### Post by steve.horsley on 2006-05-18
Install the package **bum.** It's in synaptic (multiverse, I think). Then go System->Administration->Boot Up Manager. That's a nice way to control which services get started.

Google for **sysv init** to find explanations on how it all gets started. This is not about installing kernel moduled though - it's about starting service processes - but bluetooth is one of hte ones bum says is there.

---

### Post by dbw on 2006-05-18
If you want to deactivate booting processes, one of the simplest and most complete methods is delineated in [this]("http://ubuntuforums.org/showthread.php?t=89491&referrerid=48700") thread.  If you want to go one step further, you can recompile your kernel, removing unneeded components.  It is not that difficult, and it will give you a better idea of what is going on in your box.  I also noticed a slight improvement in memory usage.  [This howto]("http://ubuntuforums.org/showthread.php?t=85064&referrerid=48700") will give you an excellent step-by-step walk-through of this process.

---

