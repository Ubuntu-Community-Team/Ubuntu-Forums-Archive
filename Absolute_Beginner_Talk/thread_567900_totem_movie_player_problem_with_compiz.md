---
title: "totem movie player problem with compiz"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-10-05
Compiz seems to be messing with totem movie player, whenever I play a file the screen is black, and when I full screen it I just get a fractured image of my desktop. It works fine when compiz is off.

Any idea what the problem is?

---

### Post by mysticmatrix on 2007-10-05
> **Ludford said:**
> Compiz seems to be messing with totem movie player, whenever I play a file the screen is black, and when I full screen it I just get a fractured image of my desktop. It works fine when compiz is off.

Any idea what the problem is?

The problem is your graphics card drivers don't support overlay of video. Too geeky term.
Short and simple, its fault of your graphics manufacturer, probably ATI or Intel. So you cannot use hardware acceleration for your video's at same time using Compiz.
To fix this, open terminal and type

```
gstreamer-properties
``` 

From Video output box, select No XV. (It is a option something like that)

This will fix your video problem, but you might see a little choppy video, depending on your CPU power.

---

