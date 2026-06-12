---
title: "xorg, dual screen, mouse pointer wierdness"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by getut on 2006-12-19
I am seeing some weirdness with xorg. And right off the bat, sorry for the long post. This is a simple problem, but difficult to explain properly.

I have successfully had the fglrx drivers running with full 3d acceleration for quite some time even with dual screen output, but have been tinkering for weeks trying to get it fully tweaked to my liking.

My setup is the laptop panel (main screen) to the left of my 24" lcd (secondary screen). It has been running well but until the last few days I could never get the 24" lcd to run at full resolution which is 1920x1200. It always ran at 1680x1050, the same as the laptop panel which made the 24" screen look horrible.

I have finally managed to get all working together now. 3d acceleration is working, dual screen is working with screen 0 at 1680x1050 and the screen 1 at 1920x1200. But now I am having mouse pointer issues and I will try my best to explain this.

With screen 1 being a larger resolution than screen 0, it seems that xorg has lined the tops of screen up at the same point. In other words If I put the mouse at the very top of screen 0 and move right to screen 1, it winds up at the top of screen 1. The bottom is a different story (as it should be)... If I put the mouse on the bottom of screen 0 and move toward screen 1, the mouse is not at the bottom of screen 1 but about an inch from the bottom. None of this is a problem with the exception of the effect it has on the mouse.

If I move the mouse anywhere in that section of screen 1 that has no equivalent on screen 0, then when I move the mouse pointer back to screen 0, the graphic of the mouse pointer is no longer lined up with where the mouse point "actually" is. In other words if I were to click on an email with the mouse pointer graphic, it will actually select an email a few lines down from where the graphic is pointing.

Weird huh. Can anyone help?

---

### Post by getut on 2006-12-19
Oh.. I forgot to mention. I'm still using the above setup because the workaround is quite easy.

When the mouse pointer graphic and the actual pointer get misaligned, I can just "bump" the top of screen 1 with the pointer and it seems to line them back up again.

---

### Post by marcele on 2006-12-19
This is a known bug with the fglrx drivers. Unfortunately there is no workaround.

---

