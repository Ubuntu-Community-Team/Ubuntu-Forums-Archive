---
title: "Virtualbox Fullscreen help please"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by 71CH on 2007-10-17
I wasn't sure where to post this so mods please move if necessary.  I was wondering if someone could tell me what the easiest way to switch between workspaces is when you have virtualbox in fullscreen mode.  For example if I'm on XP via virtualbox in fullscreen mode I always have to exit fullscreen mode in order to switch to a different workspace.  Is there an easier way to do this?  Alt+CTRL <arrow> does not work in fullscreen mode.  Thanks.

---

### Post by 71CH on 2007-10-17
Another question might be in normal, non-fullscreen mode is it possible to have windows xp without the virtualbox menu bar and the side windows.  In other words, a sort of picture-in-picture option of virtualbox within ubuntu without the things that make it look like i'm using virtualbox.  I hope I'm making sense...

---

### Post by Beggar on 2007-10-17
In response to the first post, there is an option to disable sending special key combos to virtualbox machines window, go File -> preferences ->input -> disable auto-capture keyboard.

As for the second post, I have seen this done with VMWare, but not virtualbox.

---

### Post by mk4umha on 2007-11-12
> **Beggar said:**
> In response to the first post, there is an option to disable sending special key combos to virtualbox machines window, go File -> preferences ->input -> disable auto-capture keyboard.

As for the second post, I have seen this done with VMWare, but not virtualbox.

hit your special key once, then hit CTRL-ALT-Arrow. that's how I do it without going out of full screen.

I've noticed however, If i go in and out of full screen, my video drawing of windows in my x-sessions starts to deteriorate to the point that it does not update. What i mean by update is, if i move a window with the mouse, the window does not get redrawn.  Has anyone seen this?

---

### Post by ariel on 2007-11-23
> **Beggar said:**
> In response to the first post, there is an option to disable sending special key combos to virtualbox machines window, go File -> preferences ->input -> disable auto-capture keyboard.

As for the second post, I have seen this done with VMWare, but not virtualbox.


For the second one:

VBoxManage setextradata global GUI/Customizations noMenuBar,noStatusBar

---

