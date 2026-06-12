---
title: "All sound output stopped working, after a reboot..."
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by nzk on 2007-07-23
I had rebooted and was about to watch a video in mplayer, but the sound didn't work. Thinking some volume settings had messed up, I fired up alsamixer, and only one was on. I turned them all up, but it still doesn't work. I tried using sox to play a music file, and it said "/dev/dsp in use or not available".


As my computer is literally hanging by a string, and I have blank media to recover it (I am on vacation), I would really like it to hold for two more days as I fly back home.



Any ideas what has happened? The sound device is still listed in lspci.

---

### Post by nzk on 2007-07-23
Bump...

---

### Post by laidback on 2007-07-23
Have a look at all your applications that use sound, you may find that one of then has mute on...this happened to me in 6.06.

---

### Post by nzk on 2007-07-23
As much as I doubt that mplayer, sox, and firefox all have mute on, I'll take a look.

---

### Post by laidback on 2007-07-23
Agreed, but worth a look.

---

### Post by gerrymoth on 2007-07-24
I find I lose sound if I'm watching a video from youtube and while I still have firefox open I open amarok to listen to some music and when I return to firefox I have no sound.

I have to reboot to get sound back again.

---

