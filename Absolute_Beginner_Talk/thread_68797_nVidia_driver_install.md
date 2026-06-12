---
title: "nVidia driver install"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by sonyack on 2005-09-24
Well, I'm making headway, in little tiny steps, but now there is for me a huge step.  I read the tutorial on installing the bundled nVidia drivers and I did it successfully [!] as the nVidia splashscreen came up.  But this did not make any difference in graphics performance.  Not that I have here much to test that - all I have is the visualization that gets displayed when the little .wav file I can play in Totem plays and that display is... shall we say, primitive?  So I would like to try to install the updated drivers for Linux that I got from nVidia.  The .tar.gz file and its extracted stuff I parked in the home folder.  The readme file is very comprehensive [if only I were comprehending :)].

But first, I would like to know where is the best place to put such files [apps and devices and so on that do not come with Ubuntu and are not found in Synaptic].  And I would like to know if I should remove the drivers that I installed via Synaptic before I put these new ones in, once I figure out how to do that.

---

### Post by PsyberOneZero on 2005-09-24
The "bundled nVidia drivers" (I'm assuming you mean nvidia-glx), don't really do much for 2D acceleration, but they work wonders for 3D acceleration. 

The guys here at Ubuntu are doing a good job with keeping new-ish drivers in the repo's so I wouldn't mess with the .tar.gz version unless you can't get the .deb version to work at all.

I personally have a folder in my Home directory where I put all of my source code/projects just to keep everything organized

Here are a couple of threads/HOWTO's on working with the nvidia kernel drivers
[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368) 
[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924)

---

### Post by sonyack on 2005-09-24
OK, thanks for the info.  I'll be using the drivers fro Ubuntu until I get some more practice with things - it ain't broke [yet], so I'm not gonna fix it.  But later on, I think I will try for the drivers from nVidia, as they night provide certain features I like to have, like a gpu temp monitor...at least I think they do.

---

