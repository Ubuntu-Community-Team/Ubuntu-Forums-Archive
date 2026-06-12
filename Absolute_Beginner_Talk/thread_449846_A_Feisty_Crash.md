---
title: "A Feisty Crash"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Astrodan on 2007-05-20
Can someone make some suggestions about recovery from a crash.  My otherwise nicely working Fiesty stopped cold today when I clicked to open Evolution.   I figured a reboot would fix me, but, I got a error which instructed me to manually run some kind of diagnostic. (Please forgive absolute beginner for not remembering the name)  I gave it the root password and followed the suggested fixes.  It did its thing and put a couple of small files in the Lost and Found.  This got me back to where I am presently, however,  my sound doesn't work properly and the system hangs everytime I try using items like System >Preferences > Sound. 

Is there some place to look to revert or recover?  


Thanks in advance,
Dan

---

### Post by Borzo on 2007-05-21
This is what happens when you reboot not using the system shutdown command, the filesystem sometimes gets corrupt. In theory the filesystem should have been checked after this automatically(?) . 

I'm not sure what you could have done, I don't think you manually checked the filesystem since it would need to be unmounted...but the fact that you have files in /lost+found means that some files were corrupt and fsck  recovered ( or tried to ) and copied them there, try copying those files to their original locations.

Anyhow, in the future, try ctrl+alt+F1 to switch to console and see if you can login and reboot your system with the reboot command. If it works, then this is much safer in such situations.

Good Luck. ;)

---

### Post by Astrodan on 2007-05-27
Well, it is 6 days later, and, I still have yet to solve the audio problem.  Thank you Borzo for offering the advice on Ctrl, Alt, F1.  I have used it, nice.  The filecheck did uncover the mistake and following it's instructions, did get my system to where I am today.   The audio is still not working on Feisty.

I have discovered that some kind of activity is being reported on syslogd, and, I am not savvy enough to know what it means.  I feel certain it has something to do with the sound not working.  Perhaps a virus??  I'll do a second post and send some of report.

Right now, I have used ESC at the grub boot to revert to 6.10.   Yes, the sound works perfectly here.:D   Now my question is, how do I force the original upgrade from here to reload the packages??  I have tried reloading the sound packages using Synaptic without finding the problem file. 

Thanks in advance,
Dan

---

