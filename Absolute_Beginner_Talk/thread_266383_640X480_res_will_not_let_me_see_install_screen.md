---
title: "640X480 res will not let me see install screen"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by wordmaster on 2006-09-27
Trying to install on PC. Boot from CD and can only get VGA resolution. When screens come up during install, I can only see a part of the window. Can't see buttons at bottom to clik "forward", etc. Any help would be appreciated.

---

### Post by darrenm on 2006-09-27
Are you using the desktop or alternate CD to install?

---

### Post by wordmaster on 2006-09-27
I downloaded the system, burnt it to a CD, use the CD to boot up, and double click the install icon on the screen to start the installation.

---

### Post by siggieric on 2006-09-27
hello i got the same problem djust use your mouse and drag upp thene you can hold on hope this work:p

---

### Post by wordmaster on 2006-09-27
I tried dragging with my mouse, but that didn't work. Tried holding down alt while dragging,  but no good. Tried changing res, but would not let me. Any other ideas?

---

### Post by steve.horsley on 2006-09-27
You could open a terminal (Applictions->Accessories->Terminal) and enter this command:
**sudo dpkg-reconfigure xserver-xorg**
and answer a bucket-load of tricky questions. Just accept the default answers until you get to the questions about screen resolution. After you finish that, press Alt-Ctrl-Backspace to reset the GUI (takes maybe 10 seconds to come back again).

If that fails, try download the "alternate" installer CD, which is a text mode installer - much more reliable in my opinion.

---

