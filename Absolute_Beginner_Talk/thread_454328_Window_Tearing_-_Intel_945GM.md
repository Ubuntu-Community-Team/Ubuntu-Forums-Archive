---
title: "Window Tearing - Intel 945GM"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-05-25
I am experiencing tearing when I move windows in both Metacity and Beryl.

I have an Intel Mobile 945GM video card setup on 915resolution. I got a good 
resolution, but the tearing can be very annoying.

Thanks for your help!

---

### Post by dan171717 on 2007-05-25
what do you mean tearing??

---

### Post by shanepardue on 2007-05-25
When I move windows around, there's a line of slowness that runs through horizontally through the window. I think that's the best I can explain the term "tearing".

---

### Post by Enverex on 2007-05-25
Are you using Beryl?

---

### Post by shanepardue on 2007-05-25
I got window tearing with or without Beryl.

---

### Post by NilsE on 2007-05-25
I have a Intel 945GM on a Dell laptop and don't have any such problem. Out of the box I did also have to use the 915resolution to get the widescreen but that was no big deal.

On XP at one time I had the same problem but that was when I had selected other than the native resolution for the monitor.

Make sure the resolution you set with 915resolution is the exact match for what is best on your monitor.  Also check the refresh rate.  If it expects say 60hz and gets less sent it could also cause the problem.

One more thing, are you using the i810 driver or the new Intel driver.  Both are in the repository so  if you are using one try the other and see what happens.  By the way, via Synaptic when you install one it automatically uninstalls the other so it is easy to go back and forth.  Also, on the new Intel driver you won't need 915resolution.

Let me know how this works and what you final solution is.

---

### Post by shanepardue on 2007-05-25
I haven't used intel much..What's the "new intel driver" called in the repos? I'd have to try that. I appreciate your help!

---

### Post by Atomic Dog on 2007-05-25
You don't need to use 915 res any longer...

For Feisty xserver-xorg-video-intel is in the repository. Open Synaptic Pkg Mgr and just do a search for "intel" and you'll find it on the list. Check it and it will uninstall the i810 driver. Reboot and you'll have 1280x800.

This may very well solve the issues as I noticed some slight tearing myself using 915.

---

### Post by shanepardue on 2007-05-25
> **Atomic Dog said:**
> You don't need to use 915 res any longer...

For Feisty xserver-xorg-video-intel is in the repository. Open Synaptic Pkg Mgr and just do a search for "intel" and you'll find it on the list. Check it and it will uninstall the i810 driver. Reboot and you'll have 1280x800.

This may very well solve the issues as I noticed some slight tearing myself using 915.
That fixed it! Thanks for your help everyone!

---

### Post by Atomic Dog on 2007-05-25
Woohoo!  Glad it worked for you.  :)

---

### Post by shanepardue on 2007-05-27
Actually, I thought there was less tearing, but I'm finding there is more than before. I've since reverted back to the 
i810 driver. Sorry for the false hope!

I'm having a hard time with this intel driver and it seems it's a little less supported than nvidia despite it's open 
driver.

---

### Post by shanepardue on 2007-05-31
Any ideas?

---

### Post by shanepardue on 2007-07-06
One last bump! I'm tired of the horizontal window tearing!

---

### Post by okke on 2007-08-07
I experience this also. I can see it also in videos.

---

### Post by shanepardue on 2007-08-13
My guess is it's either a product of poor quality hardware or drivers

---

### Post by -X- on 2007-08-17
Enable v-sync.

---

### Post by shanepardue on 2007-08-17
> **-X- said:**
> Enable v-sync.
That's already set.

::edit - It's just a poor quality video card or screen.

---

### Post by apauloisdead on 2007-10-10
Bump.



I'm having the same problem, did anyone ever find a solution?

---

### Post by shanepardue on 2007-10-28
I tried messing around with driconf, didn't do much at all. Anyone get rid of the annoying tearing?

---

### Post by apauloisdead on 2007-12-04
Bump.


Anything anyone? I'm still having this problem.

---

