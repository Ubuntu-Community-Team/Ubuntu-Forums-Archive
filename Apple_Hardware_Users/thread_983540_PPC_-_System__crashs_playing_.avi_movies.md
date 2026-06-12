---
title: "PPC - System  crashs playing .avi movies"
date: 2008-11-15
forum: Apple Hardware Users
---

### Post by tiresia on 2008-11-15
Apple PowerMac 2x2.5 GHz, 8 GB Memory (Juni 2004)

I can play .avi movies, but regularly it happens that the system crash - sometimes after few minutes. I have still a desktop, but I can't do anything, I can just move the mouse, and audio keeps going on. I had a look in the log files, but I can't find anything.
Since I don't find in this forum anyone who had the same problem, I guess that it has more with powerpc64 to do. 
I suspect it depends on the scaling governor and/or the demons - but it happens with powernowd and with cpudyn, with Totem, VLC and MPlayer, and with Debian (Lenny) and Ubuntu (Hardy and Intrepid)
And of course can depend on X.
Does anyone has the same issue?

---

### Post by stream303 on 2008-11-16
I can only speculate and maybe try to narrow the problem down.

Does it crash when playing the .avi's solely from the dvd, or does it do it when played from the hard disk?

Can you run top or some other resource monitor while it is playing to see if something is spiking the cpu when it happens?  (my fav is actually htop these days)

Does it happen if you run from alsa instead of pulseaudio?

Can you drop your video bit depth to 16 (not that you'd want to keep it like that) to see if it may point to something in the video overtaxing the system?

Again, all just stuff I'd experiment with since I admittedly don't have the knowledge to pinpoint it outright.

---

### Post by tiresia on 2008-11-16
Stream, thanks for your answer. Yes, it happens when I watch an avi movie from my HD. I monitored my system with 'top'. Totem takes between 8 and 12 % of the CPU power. And I can use at the same time different programs without problems. It happens suddenly, without any apparent reasons. 
Sometime I can still move the mouse, and the audio is still on (I do use ALSA) Therefore I suspect that it has more to do with the scaling governor(???), that it is not able to adapt the cpu's power adequately(???).

I'm planning to try also with Fedora - just to see if it creates the same problem. Or maybe I should try to run a different kernel.
Unfortunately there are not so many linux powerpc-users, that run ubuntu/debian on the same type of computer as mine.

---

### Post by stream303 on 2008-11-17
> **tiresia said:**
> Stream, thanks for your answer. Yes, it happens when I watch an avi movie from my HD. I monitored my system with 'top'.

While you're in top, press the "1" key to make sure that both your cpu's show up.  All the recent smp-enabled kernels should do this by default, but it might be nice to doublecheck for peace of mind.

> Therefore I suspect that it has more to do with the scaling governor(???), that it is not able to adapt the cpu's power adequately(???).

If you suspect this, it is pretty easy to check.  Just remove powernowd and you'll be running full speed all the time.  If your avi's play back ok, then maybe consider installing cpudyn instead of powernowd, and see if the reduced latency of cpudyn helps.  (cpudyn only has two states - full speed and half-speed and switches rapidly)

If you install cpudyn from synaptic or apt-get, it should automatically remove powernowd for you, so it saves you a step.

Note that you may want to see if powernowd is actually working in the first place!  If you right click the top panel and "add to panel" the cpu frequency monitoring applet, and your machine is already running full speed all the time even when it should be idle, then powernowd is not working as it should in the first place.  (there is a config file you can change to make it work if you want to, or just stick to cpudyn which I've never heard of failing.)

In fact, because of your multiple cpu's, you may want to add TWO frequency monitoring applets, (change the second applet's prefs to monitor cpu1) to see if anything weird is going on with smp.  Top will show this too if you hit the "1" key while running it.

---

