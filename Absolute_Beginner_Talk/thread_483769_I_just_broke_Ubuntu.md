---
title: "I just broke Ubuntu"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ultimadrift on 2007-06-25
So recently installing ubuntu and looked at a guide to display dual monitor
now i broke it somehow...it wouldnt boot wonder how imma fix this...reinstall or reformat?
also trying to reformat doesnt work for some reason
I need some help so thanks guys :)

---

### Post by dfreer on 2007-06-25
Can you tell us how it is broken exactly, or at least how far along in the boot process it gets? I'm assuming since you were messing with dual monitors, and therefore likely messed up /etc/X11/xorg.conf, the x server is simply crashing on you. If this is the case, you should be able to reach a login prompt by hitting <Ctrl><Alt><F5>, ten login and reconfigure the x server.
However, without knowing more details it is kinda hard to troubleshoot your problem. If you reformat, you will need to reinstall the OS (as formatting deletes everything), and if you want to reinstall it is best to reformat (although in some cases it is not needed, like if you have a seperate /home partition, you would not need to reformat it). In general, unless you get a corrupted install (probably not your case, if it was working fine before you messed with it), or you don't want to learn how to fix things and just want it to work, there's no need for a reinstall :)

---

### Post by bapoumba on 2007-06-25
Thread moved to the "Absolute Beginner Talk" support forum.

---

### Post by ultimadrift on 2007-06-25
So i gave up on trying for dual monitors i fixed with ur help guys thanks :) i think that i got it
Dual monitors are pretty hard to set up in this OS lol...Anyways Ive unistalled ubuntu from my main computer and im installing it on my backup with compiz with a 32" LCD TV and it looks really good but one thing i cant get it to 1367x768 thanks for helping out guys :)

---

### Post by dfreer on 2007-06-25
Dual monitors with my nvidia card is as simply as using the nvidia-settings program, clicking enable on the secondary monitor, and save the settings to file. Don't blame it on the OS :p

As for your backup pc, again, if you need help you have to give us more information. what video card do you have in your pc, what model is your TV, what have you tried to get it to display 1367x768 (did you mean 1366x768, btw. it should be using 1366x768 as far as I can tell, but again I don't know what model you have).

---

