---
title: "Screensaver still there.."
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by spock84 on 2006-10-11
I've got this problem where I'll get a blank (black) screen after like 10 minutes idle (like when watching a movie or something) even if I've turned off both the screensaver and the power managment thingie.. What's wrong?

---

### Post by zappa on 2006-10-11
My guess is that you put your screensaver to 'blank'?

---

### Post by spock84 on 2006-10-11
It IS set to blank, BUT "Set session as idle" is set to 2 hours, and I've unchecked the "Activate screensaver when session is idle" option.

---

### Post by pistcivet on 2006-10-11
Add this section to /etc/X11/xorg.conf:
```
Section "ServerFlags"
	Option	    "blank time" "0"
	Option	    "standby time" "0"
	Option	    "suspend time" "0"
	Option	    "off time" "0"
EndSection
```
Resolved the problem for me.

---

### Post by spock84 on 2006-10-11
Thank you! I think that did the trick.

---

