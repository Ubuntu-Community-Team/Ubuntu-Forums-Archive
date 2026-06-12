---
title: "lost sound"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by alvid on 2006-07-28
I was tinkering with alsa mixer and sound control. Now I have no sound at all
no drum roll on the the boot up, no sound at all. The green speaker icon
does appear at boot. I had sound before tinkering. Does anyone have the
default settings for alsa mixer and volume control.
Thanks.

---

### Post by OU812 on 2006-07-28
Put the mouse on the menu bar. Right-click. Choose "add to panel". Look for the volume knob. Also, go to the terminal and enter

sudo alsamixer

adjust settings, particularly main and pcm. Make sure nothing is muted. Hit esc and your settings should be saved.

john

---

