---
title: "Banned sound"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Vinillum on 2008-04-07
When I enter Kubutu environment I can't hear music neither from XMMS nor Wine programs, except VLC Media Player. After about 5 minutes I get the sound working in both XMMS and Wine. In XMMS I get someting that my driver is not setup or whatever, event though it can play sounds later. What could be the problem?

---

### Post by wesleybailey on 2008-04-07
What sound driver is XMMS currently using (ALSA or OSS)? 

Here is how to check 
Options ->Preferences -> Audio I/O -> Output Plugin

---

### Post by Vinillum on 2008-04-08
Alsa

---

### Post by wesleybailey on 2008-04-08
Try changing it to OSS, and reboot to see if that helps. 

I agree it is pretty strange that it says "soundcard not configured", and then 5 mins later it starts working. But hey it is worth a shot.

---

