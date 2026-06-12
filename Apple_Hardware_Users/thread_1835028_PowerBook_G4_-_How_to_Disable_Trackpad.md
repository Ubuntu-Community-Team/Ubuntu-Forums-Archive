---
title: "PowerBook G4 - How to Disable Trackpad?"
date: 2011-08-28
forum: Apple Hardware Users
---

### Post by rhcodey on 2011-08-28
Ok, I've tried all the standard help suggestions on Ubuntu Forums and searched the forums themselves for an answer. Nothing has worked. I've tried powerpc utils, gsynaptics and a host of other apps and command line tools. I've also tried FN+F Keys. Nothing worked.

I have a PowerBook g4 that I just installed Ubuntu 10.04 upon. The trackpad screws up my typing every time, and I just want to disable the trackpad.

I've had ubuntu on this laptop before and I had a way to disable the trackpad, but after many years and a reinstall of ubuntu (10.04 in this case), I don't remember and can't find information on how to disable the trackpad. As I remember, last time I had to go into xorg.conf and modify something to "0" to disable trackpad. Xorg.conf looks completely different now from last time I modified it years ago and there is nothing I can find to modify the trackpad to disable it.

PLEASE help. I really want to use my PowerBook G4 ubuntu 10.04, but the trackpad constantly gets in the way of my typing and it is just useless with the trackpad engaged.

FYI: Gsynaptics gave me an error message when it was installed, so I can't get to system/preferences/trackpad....even though I'm not sure I can disable the whole trackpad there anyway, which is what I want to do.

Also: When I run xinput list the trackpad is listed as "ABD Mouse".

Thank you in advance.

---

### Post by rsavage on 2011-08-28
If you just need the tap disabling...

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_behaviour.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_behaviour.3F)
[http://manpages.ubuntu.com/manpages/lucid/man8/mouseemu.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/mouseemu.8.html)

---

### Post by rhcodey on 2011-08-28
That did the trick as far as the trackpad ruining my typing. Thank you.

I would still like to disable the trackpad, however. I despise the things and turn them off on any laptop I get.

Any assistance anyone could provide on how to turn this off would be much appreciated.

---

### Post by linuxopjemac on 2011-08-29
What I use in MintPPC is powerprefs. You can, correct me if I am wrong, lock the trackpad with that tool.

[http://pbbuttons.berlios.de/projects/powerprefs/gfx/pp-pmacinputs-o.png](http://pbbuttons.berlios.de/projects/powerprefs/gfx/pp-pmacinputs-o.png)

---

