---
title: "[SOLVED] Annoyance with restart"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-25
AS the title suggests restart is annoying me!

If something like software updates requests a restart it works fine. 

If I decide to restart it goes through the motions the orange bar empties and then it sits there waiting for armageddon! I have to power off and then restart it. 

Any ideas out there - other than don't restart! :D

---

### Post by ggaaron on 2007-06-25
Interupt grub, press e to edit right entry, then select the longest line and press e, delete quiet and splash, press enter (or esc I don't remember) and b for boot. Now it will tell you what it is actually doing instead of shutting down.

---

### Post by forestpixie on 2007-06-25
which would be the right entry to edit to show me whats going on on restart?

the one I booted with in the first place?

---

### Post by ggaaron on 2007-06-25
Probably the first one, the one you use normally to boot. This will change settings only for one time, nothing will change globally=)

---

### Post by forestpixie on 2007-06-25
cheers - i'll try that to see what's stopping it :)

---

### Post by forestpixie on 2007-06-26
Ok well I did that

on restart everything gets an OK until 

```
NetworkManager: <WARNING> nm_hal_deint () libhal shutdown failed - Connection is closed
*Will now restart
[103.370674] Restarting System
```


and then it doesn't ?

it's not a massive problem - but it is annoying if I forget and restart instead of shut down!

---

### Post by ggaaron on 2007-06-26
You can post a bug report, and maybe it will be fixed.

---

### Post by forestpixie on 2007-06-26
that's what I thought. thanks for your help :D

---

### Post by coolen on 2007-06-26
> **forestpixie said:**
> AS the title suggests restart is annoying me!

If something like software updates requests a restart it works fine. 

If I decide to restart it goes through the motions the orange bar empties and then it sits there waiting for armageddon! I have to power off and then restart it. 

Any ideas out there - other than don't restart! :D

Sounds to me like Linux can't halt your system. If you have an older computer (I have one from the turn of the century that doesn't support it), this may be the problem.
It's also possible that you don't have the right modules loaded in your kernel. I don't pretend to know much of anything about kernel configurations, but I think you're looking for ACPI support.
Try this command:
lsmod | grep acpi
It might yield some useful information, and hopefully a more experienced forum member can help you out further.

If you'd prefer, try this:
sudo shutdown -P now
That'll (hopefully) cause your system to power down. Just to check if you can.

---

### Post by forestpixie on 2007-06-27
it's only halting if I restart myself - shutdown and software asking for a restart works fine.

---

### Post by Golyadkin on 2007-06-27
I had the same problem with Feisty 7.04 beta 32bit, but when I switched to the 64bit final version, the problem magically disappeared.

---

### Post by forestpixie on 2007-06-27
heh heh - doesn't annoy me enough yet to get into new mobo and processors :D

I'm sure it'll come out in the wash!

---

### Post by Golyadkin on 2007-06-27
I read somewhere that deactivating "powernowd" helps solving this problem. You can give it a try.

---

### Post by forestpixie on 2007-06-27
i'll search for that then and have a look - thanks 

:lolflag:

---

### Post by forestpixie on 2007-07-16
Ok - still have the same problem - I can now say that it seems to only be a Linux issue though - I've been looking at other distros - I've run live cds for

Knoppix
Fedora
PCLinux

and all have the same problem as Ubuntu -none of them allow me to restart, win still does though - at least it did last week :)

Appear not to have powernow running - installed bum it doesn't show it 

Any thoughts would be appreciated and TIA

---

### Post by forestpixie on 2007-09-05
But Gutsy lets restart work - or at least tribe 5 does

---

