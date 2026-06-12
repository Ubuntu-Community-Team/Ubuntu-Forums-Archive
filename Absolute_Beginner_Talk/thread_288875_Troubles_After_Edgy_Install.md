---
title: "Troubles After Edgy Install"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by drewprew on 2006-10-30
After loading edgy on my latitude X300 this weekend (process 80% complete as of 3 am this morning and after 6 hours of fitful sleep now getting back at it).

Here is a list of the problems I still have or created in process:

1. Media Bay extra speakers not putting out sound, regular laptop speakers do
2. Shutdown & Restart icons vanished (not sure when, but I think after I installed some lib development packages, or when I installed amarok from source?)
3. This isn't important now, but after installing the newest gtkpod, it flashes briefly upon opening and then closes (all this happens in the blink of an eye). I don't really mind, Amarok is managing my Ipod mini perfectly now.

Any help with either of these issues would be great, also, I forgot to mention, I'm a total noob, I had to research how to use cp.

---

### Post by jkvv_1973 on 2006-10-30
was it an upgrade style install from Dapper? Someone in the forum highly recommended this type of install of Edgy rather than starting from scratch...

---

### Post by blissfulpenguin on 2006-10-30
I've only got about a year under my belt, and I am not familiar with your hardware, but it sounds like to me either:

A.  You need to adjust the volume settings for that particular port.  You can double-click the volume icon by the clock and then try to fiddle with all the switches available.  If this doesn't work, go under the menu and select preferences.  Here you can add devices to the mixer.  If all of this fails you could have a module problem.  (see B).

B.  The sound is not coming out because you have two sound cards, one for laptop speakers and another for "Media Bay."  open a terminal, and enter the command "lspci".  This will list all hardware devices.  You're looking for more than one "multimedia/audio controller."
1.  If you do find more than one, you need to find out what modules are loaded into the kernel.  this is done with the command lsmod.  If you don't find modules matching both cards, then you need to try to find a driver for the missing module.  Most likely this is not the case.

..if you've made it to this point, please copy/paste the output of both the lspci and lsmod commands in reply to this thread.  this will give us (the community) the debugging info we need to continue working on your problem.

Hope this helps, and I am open to any questions you have.

Just an average Ubuntu user.
Josh

---

