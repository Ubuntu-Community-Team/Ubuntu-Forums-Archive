---
title: "System slowdowns"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-06-15
Hi All

Need a little help with system slowdowns; using Xubuntu 6.10 Edgy on a Dell L1000R with a i810e graphics card.  

The slowness started a few weeks ago, but I am not sure what precipitated it; 

I did notice something odd, though.  I had a small issue earlier with my panels disappearing.  When the panels were gone, I noticed that I seemed to be traveling at warp speeds comparatively speaking.  

What information do you need to help me on this diagnosis?

---

### Post by Happy_Man on 2007-06-15
Well, it means gnome-panel has become a memory sink. Perfectly normal for some people; when it happens, open up a terminal and type: ```
killall gnome-panel
``` Same thing happened to me. Eventually I got so ticked at gnome-panel I switched to KDE.

---

### Post by Xoanan on 2007-06-15
> **Happy_Man said:**
> Well, it means gnome-panel has become a memory sink. Perfectly normal for some people; when it happens, open up a terminal and type: ```
killall gnome-panel
``` Same thing happened to me. Eventually I got so ticked at gnome-panel I switched to KDE.

That&#347; a nice idea, but I am using an XFCE panel.  I will try a variant of the command

---

### Post by Happy_Man on 2007-06-15
> **Xoanan said:**
> That&#347; a nice idea, but I am using an XFCE panel.  I will try a variant of the command
Sorry, didn't see that you were using Xubuntu. The principle still applies though.

---

### Post by Xoanan on 2007-06-15
> **Happy_Man said:**
> Sorry, didn't see that you were using Xubuntu. The principle still applies though.

Yep, I found the command.  At first I lost all of my icons; the second time, it just knocked out the panels.  

I now have FF lauched and I had 4 tabs open at the same time!!!

Now the next question is, how do we make the panels take up less memory? I rather like the panels.  

I could take a couple of apps off of the top and bottom panels, I suppose.

---

### Post by Xoanan on 2007-06-16
Update;

I have removed a few things from the panels;  I removed 1 desktop(leaving me with 3) on the bottom panel and I removed Mozilla and the CPU usage meter from the top panel.

I left my machine on all night and came back to it this morning and I am traveling at warp 9 again!



Thank you!!!!:D:D:D:D:D

---

