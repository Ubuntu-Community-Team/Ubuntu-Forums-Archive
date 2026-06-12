---
title: "Windows shared across workspaces, disable?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Jadd on 2008-03-21
I'm running Ubuntu Gutsy and Compiz Fusion, with the cube enabled.

What's been annoying me for ages is how too many windows are shared across workspaces, and across taskbar panels. For example, if I open Amarok, it is slightly too large for my resolution, and about two pixels width of the window appears in the workspace to the right. That means, the task bar in the workspace to the right shows amarok, but clicking on it will only display the two pixels width of the window, if I want to use Amarok, I have to switch to the workspace to the left to see most of the window.

What I would really like is for the window sharing between workspaces to continue, but to only display the window title in the task bar if at least 10% of the window is in the current workspace. If I can't do that, can I simply disable window sharing completely? Thanks in advance.

---

### Post by Jadd on 2008-05-14
Bump.

---

### Post by prshah on 2008-05-14
> **Jadd said:**
> 
What I would really like is for the window sharing between workspaces to continue, but to only display the window title in the task bar if at least 10% of the window is in the current workspace. If I can't do that, can I simply disable window sharing completely? Thanks in advance.

Since you are running Compiz, there's a third option; use the "Place Windows" setting in the Compiz settings manager, and choose "Centered" as the default placement.

If you don't like that setting for all windows, you can choose the next tab "Fixed Window Placement" and setup a specific placement for Amarok alone.

Can't help with your options 1 & 2; hope the work around above will help.

---

### Post by Jadd on 2008-05-15
Thanks for that, but even with centered on, Amarok still starts on two workspaces, 99% on the first workspace, and 1% on the other. It's driving me nuts!

---

### Post by prshah on 2008-05-15
> **Jadd said:**
> Thanks for that, but even with centered on, Amarok still starts on two workspaces, 99% on the first workspace, and 1% on the other. It's driving me nuts!

Ran into the same problem today; realized first hand how irritating it can be:

THE GOOD NEWS:

System-Preferences-Advanced desktop effects settings-Category Window Management-Put-Misc Options-Avoid offscreen

Well?

---

### Post by Jadd on 2008-05-16
Thanks for that, PRShah. Unfortunately, Amarok's window is just slightly too big to fit on one workspace, so using [put](http://wiki.compiz-fusion.org/Plugins/Put) to move the window doesn't solve the problem, even with the avoid offscreen option enabled. I have to manually resize and move the window, or else maximise it. Is there a plugin that would allow me to maximise certain windows automatically?

---

