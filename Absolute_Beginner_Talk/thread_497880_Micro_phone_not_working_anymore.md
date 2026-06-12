---
title: "Micro phone not working anymore"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by pcl on 2007-07-10
Hi,

My micro use to work well along with Skype. A few days ago, I did some made a few change I think in Alsamixer by typing alsamixer in the command line and I tried (blindly) to improve the micro phone volume from there. Now it's not working anymore.

Anything should I do to get the defaut sound and micro settings of Ubuntu when I first installed it?

Thanks for your help if there is an answer

...

---

### Post by black_ice on 2007-07-10
i have the same problem and hope to find solution here

however it worked well with edgy

---

### Post by PgR on 2007-07-10
Is your mic your capture source?

Start alsamixer, use tab to select "capture" and then cursor left/right until the <> highlight Mic. If it's not the capture source press space to select it.

---

### Post by black_ice on 2007-07-10
iam sure that that there isnot any muted item in the options of the alsamixer

---

### Post by PgR on 2007-07-10
That's not the same thing, pcl.

I was suggesting that alsa may be using another port as its input, rather than the mic being muted.

---

### Post by pcl on 2007-07-10
Thanks,

When moving the tab to [capture] and choosing Mic, by the way, I still can select or deselect Capture with leaving Mic Capture on... "dual capture?"

It wasn't working, I went around again, I have tried the same selecting Mic 1 or Mic 2 in [playback] view... but it's the same for two except I felt something improved with Mic 1 like some echo in my headsets....

Anything should I do? Input port are Mic 1 or 2 only or are there any other. 

I am running everything on a Dell D410.

---

### Post by pcl on 2007-07-10
Thanks,

When moving the tab to [capture] and choosing Mic, by the way, I still can select or deselect Capture with leaving Mic Capture on... "dual capture?"

It wasn't working, I went around again, I have tried the same selecting Mic 1 or Mic 2 in [playback] view... but it's the same for two except I felt something improved with Mic 1 like some echo in my headsets....

Anything should I do? Input port are Mic 1 or 2 only or are there any other. 

I am running everything on a Dell D410.

---

### Post by pcl on 2007-07-10
oKI Nevermind it works now

I moved around Alsa Mixer chose:

Mic LR Capture with sound limit set to the red (saturation?) and Capture set to Capture and Mic 1 is working.

It works!

---

