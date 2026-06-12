---
title: "Newbie Question about Virtual Terminals"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by Kasanax on 2006-02-16
When I'm working in one of the text-only virtual terminals, I can switch back and forth to any of the other text-only terminals without issue. But, when I switch out of the GUI terminal (#7) into a text-only one, and then try to switch back, I need to log in again.

Is this normal? Is there a way I can switch between the GUI and a text-only virtual terminal without having to log in? Right now, I keep a copy of gnome terminal running full screen in one of my workspaces, but I'd rather be able to switch into a virtual terminal when I need to use the command line.

Any thoughts?


UPDATE:

So, I'm not sure why this worked, but it did. I'm running Ubuntu on a Dell Latitude D400, and I upgraded the BIOS yesterday, from A06 to A08. I had to boot into windows to run the executable provided by Dell, but after upgrading, my virtual terminal issues are gone!

---

### Post by chimera on 2006-02-16
Press alt+ctrl+F1 (or alt+ctrl+F2/F3-F6). You should be in a bash shell now, without x and gnome. Now, press alt+ctrl+F7. You should return to the gnome enviroment you left before, without having to log in again.

---

### Post by steve.horsley on 2006-02-16
That is not normal, and never happens to me. Is it possible that this is the screensaver wanting you to unlock the screen, or is it the normal GDM login where you have to supply username and password?

---

### Post by Kasanax on 2006-02-16
> That is not normal, and never happens to me. Is it possible that this is the screensaver wanting you to unlock the screen, or is it the normal GDM login where you have to supply username and password?

Yeah, it's the actual login screen. It wouldn't be so bad if it was the screensaver, since it's not so much the actual having to log in that bothers me - it's the fact that all of my windows, etc. get closed...

Any other suggestions?

---

