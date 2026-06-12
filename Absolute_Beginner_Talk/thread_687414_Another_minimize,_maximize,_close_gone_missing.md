---
title: "Another minimize, maximize, close gone missing"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by DiscGo on 2008-02-04
I have gone through previous posts and I have read several comments about merging all the minimize, maximize posts but I have not seen a clear answer or solution.


I did something to screw up my minimize and maximize buttons. My problem now is that my minimize and maximize buttons are gone.  I have gone through older posts but I can not find a solution.



Any suggestions? I have gone through the custom preferences and deactivated everything but left the settings to custom and I still can not get those buttons to return. [B]
If I turn my display settings to basic, they return but on any other graphics settings, they are missing. [/B]

---

### Post by LowSky on 2008-02-04
in terminal type

```
metacity --replace
```

and they should come back

if you have ccsm installed, then look for something that say windows themes or something to that nature ( i always forget its name) and turn it on, or restore its defaults

---

### Post by DiscGo on 2008-02-04
I don't know how you guys have learned how to do all these things, but I hope to. Thanks a lot.

---

### Post by DiscGo on 2008-02-04
Wait, I was wrong. That didn't fix it. That set my settings back to normal.


When I use my custom effects, they are still missing.

---

### Post by DiscGo on 2008-02-04
I have the "windows decoration" button selected but still no minimize, maximize, or close.

---

### Post by RomeReactor on 2008-02-04
Hi. Try pressing ALT+F2 and write or paste:
```
gtk-window-decorator --replace
```

Also, did you install Emerald?

---

### Post by DiscGo on 2008-02-04
I do have "Emerald Theme Manager".


I had the maximize, minimize, close buttons with everything running at first, and then it all just stopped.

---

### Post by DiscGo on 2008-02-04
I have gone through a bunch of these threads and I can not find any solutions other than not having custom graphics, and what would be the point of that? Does anyone have a solution for this?

---

### Post by DiscGo on 2008-02-04
Here it is:


FIRST: using the Synaptic Package Manager, I downloaded EMERALD by searching for "emerald" and installing it, then

SECOND: I went to System -> Preferences -> Appearance and I selected the Visual Effects tab. Once there, I selected the Custom Preferences for Window Decoration (you can use the Filter function in the upper left corner of the CompizConfig Settings Manager window) by clicking on the Window Decoration icon and added the word "emerald" in the Command dialog box.



-------------------------------------------------


Thank you to whomever figured this out!

---

