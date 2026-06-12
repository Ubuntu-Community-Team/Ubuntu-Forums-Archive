---
title: "Whoops, borked something"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by airencracken on 2007-03-28
[http://www.ubuntuforums.org/showthread.php?t=286307](http://www.ubuntuforums.org/showthread.php?t=286307)

If you see my post in that thread I followed some instructions to install the latest version of ALSA. After I followed that guide my -11 general kernel won't boot, either normally or in recovery mode. Fortunately, my -10 general kernel does boot. However I'd like to fix the other one if at all possible.

[http://www.ubuntuforums.org/showthread.php?t=394038](http://www.ubuntuforums.org/showthread.php?t=394038)

All the problems stem from this tiny issue that keeps my ubuntu from being 100% usable. I don't care about XGL/Beryl or any of that, but headphones matter while computing in quiet environments. All that aside anyone have any ideas on how to repair the -11 kernel? I can't remember the exact error message but next time I reboot I'll write it down and append it to this post. It has something to do with the sdn module not exiting correctly or something.

---

### Post by mahy on 2007-03-28
You can try it again, leaving out the --with-cards=hda-intel thing. In any case, post the actual error message.

---

### Post by airencracken on 2007-03-28
Well, I got the -11 general kernel to boot again by reinstalling the image from Synaptic so that error message is gone. The only problem now is that I have no sound at all, and my wireless support is gone. Ugh. I have so few files that I'd need to back up that I'm considering a re-install, but I'd like to avoid that if at all possible. 

Stupid me doing stupid stuff. :)

I guess for now I'll just set the -10 general kernel as my default in grub. :/

---

### Post by airencracken on 2007-03-28
> **airencracken said:**
> Well, I got the -11 general kernel to boot again by reinstalling the image from Synaptic so that error message is gone. The only problem now is that I have no sound at all, and my wireless support is gone. Ugh. I have so few files that I'd need to back up that I'm considering a re-install, but I'd like to avoid that if at all possible. 

Stupid me doing stupid stuff. :)

I guess for now I'll just set the -10 general kernel as my default in grub. :/

Okay so I reinstalled the kernel modules, all of them and the headers for the kernel as well through Synaptic. I'm still having problems with getting the wireless to work though and the sound as well, not to mention that my original problem is still in effect. Anyone have any ideas? It seems I'm not the only l35 owner with this problem. Hopefully a fix will be in the Fiesty release. As I've said before, not the most pressing issue, however it would be nice to use my headphone/mic jacks for stuff.

---

