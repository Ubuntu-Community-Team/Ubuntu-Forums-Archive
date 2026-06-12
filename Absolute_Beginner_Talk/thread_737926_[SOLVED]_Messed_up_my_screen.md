---
title: "[SOLVED] Messed up my screen"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-03-28
Hope I explain this right.
When I turn the computer on the top bit of the screen is at the bottom and the bottoms at the top. 
I`m using gnome with compiz, emerald and awn.

---

### Post by Bablorub on 2008-03-28
Check your display settings dude:lolflag:

---

### Post by clarknova on 2008-03-28
I don't know about awn, but emerald is not exactly turn-key. You could try disabling it if you aren't finding anything useful on the forums.

You may also have some luck by updating your video drivers to the latest. I had some trouble with compiz using the nvidia driver from the repos, but I installed the latest from nvidia.com and she works pretty well now.

db

---

### Post by prshah on 2008-03-28
> **nothingspecial said:**
> Hope I explain this right.
When I turn the computer on the top bit of the screen is at the bottom and the bottoms at the top. 
I`m using gnome with compiz, emerald and awn.

If you mean that your display is upside down, try ```
sudo xrandr --rotation inverted
``` in a terminal (Applications-Accessories-Terminal)

If you mean that the display is "wrapped" around from top to bottom, adjust the v-sync on your monitor, or change your refresh rate.

---

