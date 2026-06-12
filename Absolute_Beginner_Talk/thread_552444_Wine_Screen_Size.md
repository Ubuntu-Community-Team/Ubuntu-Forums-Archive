---
title: "Wine Screen Size"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-16
I have wine running smoothly, but I have an issue that maybe someone else can solve or has been through.  

Ok, so here's the issue.

When I open MS Word or Photoshop in Wine I can get full screen, no problem.

But when I start games I can't get full screen.

Here's a screen shot of what I am seeing.

[http://img119.imageshack.us/img119/2069/screenshotxc0.jpg](http://img119.imageshack.us/img119/2069/screenshotxc0.jpg)

How can I get wine to show full screen for games?

---

### Post by buzzmandt on 2007-09-16
terminal type winecfg
go to graphics tab and make sure its not set to emulate desktop size (uncheck if it is)

---

### Post by peabody on 2007-09-16
Is this for all games, or just this particular game?  I can play the original half-life in fullscreen, although I do it from a launcher script because the game loses keyboard focus when it goes full screen.

---

### Post by ExSuSEusr on 2007-09-16
Ok, that worked.... I got full screen...

But, I lose the keyboard.  Does it in Quake III as well (yes, I know Quake is native, but it's so much easier to install under wine)... well for me anyway.

---

### Post by peabody on 2007-09-16
Time to write a launcher script so the game runs in its own X session.

---

### Post by ExSuSEusr on 2007-09-16
How is this done in Ubuntu?

---

### Post by peabody on 2007-09-16
[http://ubuntuforums.org/showthread.php?t=497332&highlight=what+I%27ve+learned+about+wine](http://ubuntuforums.org/showthread.php?t=497332&highlight=what+I%27ve+learned+about+wine)

Instructions at end.  Depending on your graphics card, you may have to log out, Ctrl+Alt+F1 to a virtuual console, sudo /etc/init.d/gdm stop from that console, and then run the script to have dri on the dedicated X.  It's what I have to do anyway.

---

