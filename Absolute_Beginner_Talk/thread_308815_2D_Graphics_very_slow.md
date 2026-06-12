---
title: "2D Graphics very slow"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by ADT on 2006-11-28
I was wondering how to speed up 2D graphics in ubuntu.
I tried running a freebasic game and it ran very slowly even though it has no opengl or 3D graphics. I think freebasic uses something called directdraw to draw 2D graphics.
In windows I had the same problem with slow 2D, the way I fixed it was to turn off vsync (not definitely sure it was vsync), I think vsync waits for the screen to be drawn before the computer starts drawing the screen again, with vsync turned off the computer was able to draw the screen constantly rather than waiting for each screen draw to finish.
Is there an option to turn off that same type of feature in ubuntu?

---

### Post by IYY on 2006-11-28
I'm not an expert on this topic, but isn't Direct Draw a part of DirectX, which is a Windows-only technology? 2D games in Linux are usually developed with SDL.

---

### Post by sir_mud on 2006-12-20
Unless it's using an external library the graphics are pure X windows.

---

