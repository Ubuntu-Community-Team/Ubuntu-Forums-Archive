---
title: "video playback delay"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by fcendejas on 2006-01-26
hi all, 1-day old ubuntu install!  
might be out of place, but any idea on why video and audio don't match in totem?  the video seems to be ahead by 1.5 seconds or so.  i think i've installed an updated nvidia driver, so its not that...

---

### Post by saubz on 2006-02-01
If you are referring to DVD playback, I had the same problems until I installed totem-xine.  Maybe it will work for you as well

```

sudo apt-get install totem-xine

```

or search synaptic for totem-xine

---

### Post by leonavas on 2008-01-06
after installing the application i dont have sound at all, do you have any suggestion for this  error message dude? well i have it in spanish but it says that there is no complements and  it cannot play the file, i was just trying to get rid of the delay at the begining of every song

---

### Post by saj0577 on 2008-01-06
> **leonavas said:**
> after installing the application i dont have sound at all, do you have any suggestion for this  error message dude? well i have it in spanish but it says that there is no complements and  it cannot play the file, i was just trying to get rid of the delay at the begining of every song

Try doing a search in add/remove for gstreamer and i tend to install them all as if you play alot of videos music you will need them at a later date anyway. Once installed restart xine.


Saj

---

