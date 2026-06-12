---
title: "Headset and Speakers"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by myst1c on 2008-01-07
Is there a way I can make my headset and my speakers both output at the same time? Or do I just need a splitter?

---

### Post by Jhongy on 2008-01-07
most likely you need a splitter, as the headphone jack usually incorporates an isolator switch that physically cuts the connection when a plug is inserted.

However, if you have an aux or line-out connection, you could use that for headphones instead.

Alternatively, there's a vague, outside chance that the headphone isolation is software controlled. if you fire up a terminal and run alsamixer, you'll likely see many more elements in there than are available via the Ubuntu volume control -- try playing with them.

---

### Post by rubicon on 2008-01-07
> **myst1c said:**
> Is there a way I can make my headset and my speakers both output at the same time? Or do I just need a splitter?
It depends. 

If you have on-board soundcard or if your soundcard have headphone jack, then probably you can get the same sound on all of its outputs, you just have to play with sliders and switches in mixer (note that some of them may be hidden -- look in preferences). I cannot say much about alsamixer app, but it is sure worth looking!

If you meet any difficulties, write to this thread. But describe your soundcard! Model and jacks on the rear side is what do matter.

---

### Post by myst1c on 2008-01-07
i'm thinking i'm just going to go for the splitters, cause i currently only have onboard sound... could you guys by chance help me get a mic to work, too?

---

### Post by rubicon on 2008-01-07
Tell us what have you already done to get it to work,

If it is onboard sound, then you must enable mic in mixer, and try to record something using gnome-sound-recorder.

---

