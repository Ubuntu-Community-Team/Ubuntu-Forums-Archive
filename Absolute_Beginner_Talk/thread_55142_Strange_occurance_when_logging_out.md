---
title: "Strange occurance when logging out?"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by OttoDestruct on 2005-08-07
Just recently Ubuntu started doing this... when I go to System > Log out  (save current setup not checked, only 'log out' selected) it logs out to GDM, then closes out of GDM to the command line for a second, then starts GDM again. Before it simply closed to GDM. Its more an annoyance than anything.

---

### Post by OttoDestruct on 2005-08-08
Ok... This is starting to get worse... I just logged out and while it was switching back into GDM, a blue screen shows up saying "I cannot start X server. OK CANCEL" Except the system locked up and I could do neither OK or CANCEL.

---

### Post by OttoDestruct on 2005-08-08
This has happened 5 times now with the crashing. For god sake someone help?

---

### Post by OttoDestruct on 2005-08-08
Surely someone of the ~30 people who have looked at this knows something?

---

### Post by cwaldbieser on 2005-08-08
It is more likely that the folks who looked at the problem do not really have enough information to go on to correct the problem.  Can you CTRL-ALT-BACKSPACE to restart X?  Can you CTRL-ALT-F1 to switch to a virtual console?  Or is the whole system locked (not just the GUI)?

---

### Post by OttoDestruct on 2005-08-08
[QUOTE=cwaldbieser]It is more likely that the folks who looked at the problem do not really have enough information to go on to correct the problem.  Can you CTRL-ALT-BACKSPACE to restart X?  Can you CTRL-ALT-F1 to switch to a virtual console?  Or is the whole system locked (not just the GUI)?[/QUOTE]

Yes I can ctrl alt backspace, yes I can ctrl alt F1. It's locking up when I log out and it flickers back to the command line, and the entire system locks up to the point where i need to hit the power.

---

### Post by RastaMahata on 2005-08-08
sudo cp /var/log/Xorg.0.log ~
gedit ~/Xorg.0.log
attach/copy-paste the file here, so we can try to help you.

---

### Post by OttoDestruct on 2005-08-08
Too long to post, had to upload it.

[Linkeh](http://blackmage.org/ottod/xorg.0.log.txt)

---

