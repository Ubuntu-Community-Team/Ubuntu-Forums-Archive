---
title: "Ubuntu Update Manager"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by fedupwithwin on 2006-10-06
Just loaded Ubuntu tonight - blew out Win XP entirely - too many problems with the updates causing my machine to crash.  So now, I load Ubuntu and guess what?  It wants to load a bunch of updates!  Well....OK I understand the need for this but, color me skeptical.  So, I looked through the requested updates and it says it wants to load a complete Linux-386 kernal - here's where the alarm bells went off - I'm running an AMD Athlon 1100Mhz CPU.  Is loading a 386 kernal going to abrubtly cause a mushroom cloud over the motherboard or Brown (Ubuntu Colored) screen of death somehow?

---

### Post by Marsolin on 2006-10-06
The i386 kernel is the right one for that processor. It shouldn't cause any issues.

---

### Post by nocturn on 2006-10-06
> **fedupwithwin said:**
> Just loaded Ubuntu tonight - blew out Win XP entirely - too many problems with the updates causing my machine to crash.  So now, I load Ubuntu and guess what?  It wants to load a bunch of updates!  Well....OK I understand the need for this but, color me skeptical.  So, I looked through the requested updates and it says it wants to load a complete Linux-386 kernal - here's where the alarm bells went off - I'm running an AMD Athlon 1100Mhz CPU.  Is loading a 386 kernal going to abrubtly cause a mushroom cloud over the motherboard or Brown (Ubuntu Colored) screen of death somehow?

The 386 kernel works on anything upward and is shared between Intel and AMD machines, so it is the default.

You can install an optimized kernel for your machine, I think linux-k7 is the right package.  After you boot that and it works, remove the linux-386 metapackage to disable future updates of the 386 kernel.

---

