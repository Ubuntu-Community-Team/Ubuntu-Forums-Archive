---
title: "Rhythmbox blocks sound other applications"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Pixilarion on 2007-01-17
While playing music in Rhythmbox, the sound coming from other applications (like Firefox, play,...) seems to be blocked. When I close Rhythmbox everything is back to normal.
Any idea how to correct it?

I'm using Xubuntu Edgy...
Thanks!
Pixilarion

---

### Post by mikewhatever on 2007-01-17
I think, depending on the sound card, you can only have one application using it.

---

### Post by Pixilarion on 2007-01-17
With OSS you're right: its support for older soudn cards is better and since I'm using an old Dell Optiplex GX1 this might be the case. However ALSA should be able to support multiple sources... The question is: does Xfce use OSS by default, and if so, where do I change it?

---

### Post by Pixilarion on 2007-01-17
Ok, seems like Rhythmbox is using ALSA since the Gnome ALSA can affect its volume while playing... However trying to use another application that uses ALSA, gets the "device busy" signal. So Rhythmbox gets a monopoly on ALSA... I wonder why...

---

