---
title: "Cant get any sound"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by the milk is sour on 2007-03-11
After being recommended ubuntu by a friend, i decided to try it out on a (very) old laptop.  Because it is an old laptop, i installed xubuntu and, despite running almost without problem, i have no sound.  Although i am somewhat of a beginner, i have checked the forums and made sure that the alsamixer has nothing muted or turned down, (as with all other volumes i can find) but it still doesnt work.  My soundcard is a cs4281 in a toshiba satellite s1700-200 by the way.  Any help would be greatly recieved.

---

### Post by vinchi007 on 2007-03-11
so does  alsamixer have devices there, like front, back, right, left, etc? and do you have all up and nothing [off]

If you have pci sound, check if listed with  $lspci

---

### Post by the milk is sour on 2007-03-11
As far as i can tell, i have nothing muted and all volumes are at 100.  It doesnt have front, back, etc though.  It has 3d control centre; depth and switch if they count? 

Its not pci sound, its onboard. It does appear as device #0 in mixer settings if that helps.

---

### Post by the milk is sour on 2007-03-12
apologies for my vague last post, i tried $lspci in the terminal, there was no response.  I did, however, notice that when the mouse tracks across the terminal, there is a clicking.  So far, this is the only sound that i have managed from ubuntu.  I can, however, still use the laptop as a cd player when it is turned off (via hot keys) without problem so i dont hthink its the speakers.

---

