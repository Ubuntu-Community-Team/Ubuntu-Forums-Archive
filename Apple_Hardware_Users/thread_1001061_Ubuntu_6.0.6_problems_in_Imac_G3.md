---
title: "Ubuntu 6.0.6 problems in Imac G3"
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by Killplay on 2008-12-03
hello everybody... i have an Imac G3 (400 mhz,256 ram,18gb, Ati Rage 128VR with 8mb of vram) with tiger OS, i try to install Ubuntu 6.0.6 in the mac, but i have a little problem (i found in internet information about the Video card, maybe is a problem with the model). When i am ready to install ubuntu and the mac read the iso image from the cd all is good... the screen of ubuntu charging the OS and next a black screen... the screen dont make nothing but i hear the "presentation music" of ubuntu, and thats all... i cant see nothing in the screen, thats is the problem. i need something of help.

greetings...

---

### Post by Duggeek on 2008-12-08
This is quickly becoming a well-known issue on the G3 iMacs. It's not the video hardware as much as the embedded monitor; the monitor is not built to automatically identify itself.

Head to [this FAQ]("https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3") for details on fixing it.

You can access the virtual terminals in Ubuntu, even if you can't see the GUI display when you hear the Ubuntu "ready" sound.

Press **Control+Option+F1** and you should (eventually) see a text-screen login prompt. In my experience, the difficulties on the GUI can slow-down the overall system... have patience.

When you save the new *xorg.conf* file and enter the 'killall' command--as seen in the FAQ--the GUI should reappear by itself.

If you happen to get it all working, try saving your working *xorg.conf* to a USB stick and keep it around for upgrading to Gutsy, Hardy or Intrepid.

Best of luck!

---

### Post by stream303 on 2008-12-08
Duggeek is right - that's probably one of the most valuable paragraphs for G3 iMac owners around.

If you can't even get to that point, you may want to stop at the second-stage yaboot boot: prompt by hitting TAB.

Then, try passing the following to get past some other issues:

```
live-nosplash-powerpc
or
live-nosplash-powerpc video=ofonly
or
live-nosplash-powerpc video=ofonly break=top
or
live-nosplash-powerpc video=ofonly break=bottom

```

If these work, you can make them permanent in /etc/yaboot.conf followed by sudo ybin -v  ... but lets see if this improves things.

---

