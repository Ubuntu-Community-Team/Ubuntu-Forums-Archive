---
title: "wine restarts my gdm"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by bakie on 2006-05-10
when i want to start a game i just do cd "where the game is" and the i do wine "name of the file"
but then when i press enter it restarts my gdm :confused: 
anyone got an idea what the problem could be?

---

### Post by pasdar1 on 2006-05-15
Hello,

Me too - whenever I try to use wine it restarts my gdm.  Similarly when I try to use Blender, it also restarts my gdm.  Any ideas???

Updated:

Since i have a nvidia video card (and tv-out) I had changed my xorg.conf early on so that my tv-out works correctly.  Today I tried changing my xorg.conf back to the orginal (when i installed ubuntu) and then tried using Blender and it worked fine!  I am guessing wine will also work - but i have yet to confirm that.  

Is it possible that my kernal is not updated to match my xorg.conf or something like that, which is causing gdm to restart when i run programs like blender and wine?  If so, please give a very step by step explanation such that a newbie like myself can figure out how to fix it!
thanks in advance!

---

### Post by bakie on 2006-05-17
i have tried to change my xorg.conf back to its original and it didnt worked. but then i reinstalled my driver and now its working again.
but i still seem to bee having one problem, when i type in "winecfg" it opens the config screen and i cant access the audio tab. when i click on the audio tab the screen closes and my terminal says:
Creating link /home/ikke/.kde/socket-ubuntu.
can't create mcop directory

can any1 help me with this problem?

---

### Post by bakie on 2006-05-17
i have fixed the problem. wine is working again and i can access the audio tab.
feels good to fix your own problem :)

---

### Post by tseliot on 2006-05-17
Reinstall the nvidia driver. It should solve the (common) problem

---

