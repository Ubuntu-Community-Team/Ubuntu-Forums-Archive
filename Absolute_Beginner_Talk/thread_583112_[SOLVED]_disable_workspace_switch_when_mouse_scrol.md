---
title: "[SOLVED] disable workspace switch when mouse scroll on screen edge?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-10-20
I have 7.10 on a laptop with a touchpad. When I place the mouse pointer at the right edge of the screen and then touch the scroll up/down section of the touchpad then Ubuntu switches workspace. That is, the same as what CTRL+ALT+left/right arrow does. The problem is that the touchpad is sensitive so (1) I do this accidentally and (2) it flips back and forth between left and right workspace many times before stopping.

So, I want to disable this. 

But I do not want to disable the vertical scroll for the touchpad in general. Nor do I want to disable having multiple workspaces to switch between. I only want to disable touchpad scroll from controlling workspace switching.

Any suggestions?

---

### Post by anemptygun on 2007-10-20
Take a look at this, see if that helps.:KS

[http://ubuntuforums.org/showthread.php?t=423723](http://ubuntuforums.org/showthread.php?t=423723)

---

### Post by gubemton on 2007-10-20
Thanks, but it didn't help. I know how to in general turn off vertical scrolling through the mouse settings. But I only want to turn off a specific scrolling action, not scrolling in general. 

I've narrowed down the problem to: CompizConfig Settings Manager > Rotate Cube. But I can't find an action to disable there. I only find the keyboard action that does the same thing (Ctrl+Alt+left/right arrow).

---

### Post by anemptygun on 2007-10-20
Sorry, i tried to find something out. But thats about all I could find...:confused:

---

### Post by mallow on 2007-10-21
Yes, this scroll thing is really annoying on laptops. I would also like to turn it off. Anyone knows a solution to this? :(

---

### Post by gubemton on 2007-10-22
The folks at the compiz forum solved this:
[http://forum.compiz-fusion.org/showthread.php?p=33069#post33069](http://forum.compiz-fusion.org/showthread.php?p=33069#post33069)

ccsm->Viewport Switcher->Desktop-based Viewport Switching->Move Next (default: scroll up) 
ccsm->Viewport Switcher->Desktop-based Viewport Switching->Move Prev (default: scroll down)

(ccsm = CompizConfig Settings Manager)

I missed those actions since they said Button 5 & Button 4 on my computer (not scroll up/down as above). But disabling them disabled the feature so all is well.

Hope this works for you too anemptygun!

---

### Post by mallow on 2007-10-22
hey, this is great. thanks for that :)

---

### Post by ~Chimera~ on 2007-12-08
Thanks Guys.  That was driving me crazy.  Thanks again.

---

