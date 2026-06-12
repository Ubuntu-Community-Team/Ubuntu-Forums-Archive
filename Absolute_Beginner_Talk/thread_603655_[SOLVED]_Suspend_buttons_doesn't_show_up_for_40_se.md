---
title: "[SOLVED] Suspend buttons doesn't show up for 40 seconds"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by petri on 2007-11-05
After an upgrade to Gutsy from Feisty the buttons doesn't show upp for about 40 seconds when I choose to shutdown the computer. Only mousepointer can be moved but it doesn't have any effect. When the buttons finally shows up there is no Suspend or Hibernate buttons visible. If I choose to Cancel and try to shut down again then they all appear and they do it instantly.

My motherboard is Asus M2A-MVP with Nvidias chipset and with nvidia-glx drivers.

---

### Post by sludge99 on 2007-11-06
i have the exact same problem on my pc. i didn't have any problems at all with any previous ubuntu versions fiesty etc. it isn't a compiz issue either i don't think because i tried disabling compiz altogether and i still had the same issues.

i have the amd64 gusty with nvidia-glx-new

Edit: if no one posts a easy answer to this i am going to file a bug report because it seems to be drastically different issue from the known
> 
Shutdown or restart hangs in Gutsy
- Thread : [http://ubuntuforums.org/showthread.php?t=591229](http://ubuntuforums.org/showthread.php?t=591229)
- Bug report : [https://bugs.launchpad.net/ubuntu/+s...22/+bug/119308](https://bugs.launchpad.net/ubuntu/+s...22/+bug/119308)

or any other known gusty bugs, and is really quite annoying. also i am fairly sure this didn't occur in beta when i first installed gusty.

---

### Post by iGeorgie on 2007-11-06
I just want to say I have exactly the same problems!
When I try to update the drivers from the Nvidia-site (or downgrade the drivers) I even got more troubles as described in another thread:

[http://ubuntuforums.org/showthread.php?t=592837&highlight=nvidia+gutsy+problem](http://ubuntuforums.org/showthread.php?t=592837&highlight=nvidia+gutsy+problem)

Hardware:
Asus P5LD2-V
PNY GeForce 7800 GT 256 Mb DDR3
2 Gb of RAM

---

### Post by sludge99 on 2007-11-06
ok i think i might of solved this
go to System->Preferences->Sessions
and check the power manager option

for me this seems to work i have logged out and back in a number of times and there is no wait. i will post back if the problem starts up again.

if the power manager option is no longer there you might of deleted it, you can add it again by
clicking Add
name:Power Manager
command:gnome-power-manager

---

### Post by petri on 2007-11-06
Thanks sludge99 it works for me! \\:D/

---

### Post by iGeorgie on 2007-11-06
You're the man! It works!

Many thanks...:)

---

