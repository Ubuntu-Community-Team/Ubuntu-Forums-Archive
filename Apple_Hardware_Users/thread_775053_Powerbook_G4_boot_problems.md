---
title: "Powerbook G4 boot problems"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by gtwnpntz on 2008-04-29
I have a 1.25Ghz PowerBook G4 (Apple calls is the 15-inch FW800), and I have been trying to run 8.04 on it. I started out with the live CD, but be unable to successfully proceed beyond yaboot, opted to run an install from the alternate CD image. Install was successful, but I'm running into the same problems, post-yaboot, as before. My current situation, following the alternate install, is that upon launching from yaboot a screen of typical ubuntu hue displays for approx. 5 seconds. This is followed by an error of "PCI: cannot allocate resource region 0 of device..." From what I've gathered this is not necessarily a problem that would halt further progress. After approx. another 5 sec what happens depends on the options I've included in yaboot. If I have no options, include video=radeon..., or  include video=radeonfb... at the yaboot prompt, the screen goes black except for a thin hazy gray line about 1 inch from the bottom. This will remain for at least 20 min (I shut it down after this point, but it could very well have gone longer.) If I include video=ofonly, a cursor will appear in the upper left and the fans will immediately run. The cursor will disappear after about 1 minute and the backlight will go off.

Any thoughts? Any progress @ this point would be very welcome. Thanks

---

### Post by stream303 on 2008-04-29
I had the same machine, only 12".  Kind of wish I had kept it to test Hardy on..

I can say that on Gutsy, I had to use the nosplash kernel parameter

```
Linux nosplash
```

at the second-stage yaboot boot: prompt.

In addition, this was the only machine I encountered where Network Manager took up 100% of the cpu time when it ran really slow and I ran TOP, (actually my favorite alternate HTOP) to see what was going on.  Not sure that this may also be happening in Hardy, but just a heads-up, since I disabled NM (rather than uninstalling it) and no more fan problems.

Perhaps try nosplash and see what happens...

---

### Post by gtwnpntz on 2008-04-29
I've tried nosplash, alone and w/ the various video options, and still no luck. It appears to have no effect on the result. Any other thoughts?

---

### Post by stream303 on 2008-04-29
This won't solve the problem, but I wonder if you get any sort of video at all from just doing a rescue boot shell at the second-stage prompt?

Hmm.. how about disabling the splash screen AND the boot messages with

```
Linux quiet nosplash
```

..running out of options ...

---

### Post by Skeeve42 on 2008-04-30
Hi!

I had success booting with

live video=ofonly

The screen remaind black for a long time but finally comes up with a nice Ubuntu desktop.

I have a PB G4 1,67GHz

---

### Post by InverseFlux on 2008-09-27
This will sound a bit odd, but I had stumbled onto this thread when troubleshooting my own issues with getting 8.04 onto my PowerBook G4, 1Ghz, 2GB RAM machine.

Repeatedly I had the same issues as the original poster, and persistence with the 'live video=ofonly' did appear to work.  I ran various commands to try and get something else to work, and somehow in coming back to the original command I had to run in order to get Dapper installed did the trick.

Hope this helps, in case others did stumble onto this thread as well.

---

