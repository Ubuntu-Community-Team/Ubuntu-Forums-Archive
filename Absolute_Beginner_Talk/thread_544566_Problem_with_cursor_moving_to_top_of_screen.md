---
title: "Problem with cursor moving to top of screen"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by littlepriest01 on 2007-09-06
I am having a weird problem. I am running 7.04, and also have compiz installed. When I move my cursor to the top right of the screen (closest to the close window button). It zooms out and displays all of the currently open windows. It's almost as if a "hot zone" is set, that I don't know about. I figured this may be something with compiz, but also could be because I'm using a gateway 285-e, and I didn't know of any installation issues with the touchpad on my laptop. If this is something, I'd love to know how to change the hot key so that I can still use it, just not every time I go to the top right corner.

---

### Post by asmoore82 on 2007-09-06
open a terminal and ...

```
~$ gconf-editor /apps/compiz/plugins/scale/allscreens/options
```
and play with the settings in there

you shouldn't have to restart compiz for the settings to take effect, but it coudn't hurt either.

---

