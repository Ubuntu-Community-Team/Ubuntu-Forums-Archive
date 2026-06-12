---
title: "[SOLVED] Why Does My Window Go Grey??"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-12
Is this a normal behavior for a window to fade to grey when it's busy doing something?  Like when I do a search in Synaptic, the entire window will go grey..  I find it really annoying to have it do that, makes me think my system is getting close to freezing or something..

If this is normal, is there a way to shut off that feature?

Many thanks!

FwF

---

### Post by vishzilla on 2008-03-12
The windows go grey when Compiz is turned on. You can turn off that feature by installing the Advanced Desktop Effects Settings from the repo.

---

### Post by superprash2003 on 2008-03-12
normally grey windows occur when your computer is busy and is temporarily not responding!!

---

### Post by PmDematagoda on 2008-03-12
> **vishzilla said:**
> The windows go grey when Compiz is turned on. You can turn off that feature by installing the Advanced Desktop Effects Settings from the repo.

Partly true, the windows go grey in Compiz-Fusion when the applications becomes unresponsive or freezes, the windows do not turn grey for any other event or a normal effect.

---

### Post by Arkenzor on 2008-03-12
To clarify, compiz (the window manager responsible for the default effects in Ubuntu) grays windows when they stop answering for some time. I think you can modify the inactivity delay by changing the "Ping Delay" in the General Options in ccsm (the compiz configuration panel, which you can install from Synaptic as compizconfig-settings-manager).

---

### Post by FreewareFan on 2008-03-12
I'd like to thank each of you for your information!!

Turned out that setting the ping delay up to 10000 worked just fine.  It only happened when the cpu hit 100% load, and the system was doing some intense 'thinking'.   

Anyways, thanks very much everyone!!

FwF

---

