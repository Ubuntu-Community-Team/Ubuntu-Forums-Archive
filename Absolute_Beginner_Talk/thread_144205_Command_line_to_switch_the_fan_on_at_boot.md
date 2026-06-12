---
title: "Command line to switch the fan on at boot"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Commuto on 2006-03-13
I already tried a few things... now I need a bit of help :oops:
I want the following command line to be executed upon every boot. Whatever a cold boot or a resume after hibernation:
```
bash -c 'echo "force_on: 1" > /proc/acpi/toshiba/fan '
```
It actually force the CPU fan so it's always on.

Well, I tried to create a script containing the related command line in /etc/rcS.d/S49Toshiba-fanstart
But the fan doesn't start upon boot :confused: 
Sorry for this frequently asked question, but the fact that it relies to a hardware feature confuses my confidence. :-k
Thanks for any help :D

---

### Post by Kurt` on 2006-03-13
This is definitely not the proper way to do this but...

You could add that command to the bottom of /etc/X11/gdm/Init/Default

Then it would definitely be on by the time X11 and gdm start :p

---

### Post by Commuto on 2006-03-14
Oaww... thanks indeed, that's a solution.
And how about a "proper" way? :-D
I'd prefer this feature to be stuck to the very low level of the laptop (runlevel?), rather than the Graphical Interface, in case one day I prefer to start through the command line, etc.

Huhu, don't know how to do it and I'm even demanding! Sorry :mrgreen:

---

