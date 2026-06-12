---
title: "nautlius windows"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by dachinster on 2007-08-05
Hi,
There is something in ubuntu that is annoying me with the default desktop manager (nautilus)

Sometimes when i have multiple windows open and they are all maximized, sometimes when i go to close the active window, the window behind closes and leaves the active window open..

It also happens when any small window opens near the taskbar. For example:
If i launch amsn, it opens in the top right hand corner of my screen but when i try to click the x to close the window, it goes from orange (active window) to white like what would happen if i clicked elsewhere and it went to the background.

Is this some sort of bug?

The only way i get around it is to move the window away from the taskbar or from the other windows. So now i never have maximised windows as i get annoyed that when i click to close one window, another will sometimes close instead

---

### Post by dachinster on 2007-08-11
am i the only one experiencing this?
i have ubuntu installed both on my desktop and a t43 ibm laptop and they both have the same problem

---

### Post by dachinster on 2007-08-12
ok, maybe people do not understand.
well i have attached two screenshots to help explain
in the first, i have amsn open.
Please note that it is touching the edge of my screen.

Any window, where the "X" to close the window touches the edges of the screen experience the following. This includes maximised windows or as you can see with amsn, just anything touching the edges of my screen.

Now, in the second screenshot, i attempt to close the window by clicking on the  "X" however all that happens, is the window is de-selected as can be seen by the fact that the title bar is no longer orange-brown, but has turned opaque.

If there was another window exactly in-line horizontally with the top of that amsn window but behind, the chances are that when i click to close amsn, the window behind will in fact close


does anyone else know about this, and can i do anything to solve this?

---

### Post by aysiu on 2007-08-12
Perhaps you should file a bug report on this:
[https://bugs.launchpad.net/ubuntu/+source/nautilus](https://bugs.launchpad.net/ubuntu/+source/nautilus)

---

### Post by asmoore82 on 2007-08-12
do you have desktop effects enabled?

---

### Post by dachinster on 2007-08-12
i have the "Work spaces as a cube" enabled
is this the problem?

---

### Post by asmoore82 on 2007-08-12
yea that's got to be it;
it's not a nautilus problem, it's a compiz problem.

---

### Post by dachinster on 2007-08-12
> **asmoore82 said:**
> yea that's got to be it;
it's not a nautilus problem, it's a compiz problem.


hmm, you seem to be correct!
after i turned off the desktop effects, the problem vanished!

---

