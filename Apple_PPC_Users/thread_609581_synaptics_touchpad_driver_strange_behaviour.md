---
title: "synaptics touchpad driver strange behaviour"
date: 2007-11-11
forum: Apple PPC Users
---

### Post by fuoco on 2007-11-11
I'm using in gutsy the exact same setup I used before in feisty and even earlier. But now in gutsy tapping doesn't work. I tracked it to the MaxTapTime option which gets set to 0 even though I have it in the config file set to 100. For some reason it doesn't set it in X startup - even though the log file states differently. I can always set it myself with synclient - but it's a bit annoying...
Anyone else knows about it ?

---

