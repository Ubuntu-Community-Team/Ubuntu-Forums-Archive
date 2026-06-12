---
title: "Gnome Screensaver Logs me Out"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-11
So, I always seem to have problems with screensavers in gnome, but now I have something going on that keeps me from opening the screensaver applet. It dumps me back at the login screen any time it tries to run.

[This person]("http://ubuntuforums.org/showthread.php?t=245655") was having the same problem as me, but they solved it by deleting ~/,xscreensaver . I don't have this file anywhere in my file system. (yes, I checked hidden files too...)

I feel like I'm in a Speed movie, where my idle time can't drop below 5 minutes, or else I have to log back in. :popcorn: Next step?

---

### Post by nikoPSK on 2008-01-11
So it's logging you out? Not just locking the session? I would recommend against deleting the ~/xscreensaver folder.

---

### Post by imaginal on 2008-01-12
I don't know, exactly what it is doing. Feels like a crash, some screen flickering, then the login like nothing happened... over and over again... Quite irritating, really. :-)

---

### Post by nikoPSK on 2008-01-12
did you do anything in particular before? has it always been like this?

---

### Post by imaginal on 2008-01-12
I think I selected a screen saver that is causing this problem. None of the power management works well with my laptop, but I've come to terms with that. Now I can't access system -> preferences -> screensaver. The second that I do, the aforementioned behavior occurs.

---

### Post by nikoPSK on 2008-01-12
Hrm, would you try reconfiguring xorg for me? That might be the issue...

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by imaginal on 2008-01-13
Reconfiguring went as planned, but to no help with my present problem. Should I have a ~/.xscreensaver folder? This is really kind of bugging me...

---

### Post by nikoPSK on 2008-01-13
> **imaginal said:**
> Reconfiguring went as planned, but to no help with my present problem. Should I have a ~/.xscreensaver folder? This is really kind of bugging me...

I don't have that folder.... so you shouldn't either. :)

Best,
nikoPSK

---

### Post by imaginal on 2008-01-14
Good to know. ;) I guess this questions really just boils down to: I can't use the gui screensaver changer to change out of a screensaver causing me problems. How do I do this manually?

---

### Post by nikoPSK on 2008-01-14
> **imaginal said:**
> Good to know. ;) I guess this questions really just boils down to: I can't use the gui screensaver changer to change out of a screensaver causing me problems. How do I do this manually?
 
most likely a command, I'll see what I can find once I get back from school. :)

---

### Post by mandyfester on 2008-03-16
Hello

I have exactly the same problem. I think that I have narrowed the issue down to opengl screensavers but they all work in full screen preview mode. One screensaver that works is the sonar one which does not use opengl.

Any help is really appreciated since the nice screensavers is the main reason why I use linux not windows ;-)

Mandy

---

### Post by btbarry on 2008-05-16
For future reference only....

Hopefully this isn't a problem for anyone any longer, but it took me a couple of hours to find a quick fix to this problem through the terminal or other means.  To return the screen saver to its default, follow these steps:

In terminal type:  gconf-editor then press enter.

Configuration Editor Window pops up.  Browse to apps/gnome-screensaver.  In right box find "mode" value.  Double click on the entry next to mode, and type Blank-only, then press enter.  You can close the window and termninal.  The screen saver should now be set back to "Blank-only" and should prevent your system from locking up when it idles out or you try to change the screen saver.  Just be sure to fix your resolution problem before you go back into screen saver, choose a cool looking screen saver, and repeat your problem all over again.

---

