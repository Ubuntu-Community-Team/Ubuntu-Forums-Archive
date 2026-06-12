---
title: "How to change Gnome display number?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Toshick on 2007-12-17
Hello all.
Where i can change gnome display number?

Preamble:
I have video card ATI Radeon X600. 
I've spend a lot of time to solve the "drivers" problem. Finally i decide to choose an open-source ati driver. After 3 days of dancing with tambourine, I make it work! But... There are a problem with DRI. Driver do not write anything abnormal to logs, but when i run glxinfo, I see than DRI is off. But at ones forum's thread I found that this problem is not only mine ([http://ubuntuforums.org/showthread.php?t=607386](http://ubuntuforums.org/showthread.php?t=607386)) 
 

I found difference at glxinfo output:
When I'm booting to normal gnome mode i have:
name of display: :3.0
display: :3 screen: 0

But in failsafe i have:
name of display: :0.0
display: :0 screen: 0

Where i should change preferences (conf file) to make them both use 0 display number?

Thanks

---

### Post by Toshick on 2007-12-17
Does anybody knows?

---

### Post by Lord_Dicranius on 2007-12-17
Not sure I know which display number it is that you're referring to :-\  What else is on the screen when this display number is shown?

---

### Post by Toshick on 2007-12-17
you can try glxinfo and you'll see it at first lines

---

### Post by Lord_Dicranius on 2007-12-17
I'm not in front of an Ubuntu machine, so bear with me, I'm going by what I can find online (sitting in front of a WinXP machine at work right now).  I found the man page for glxinfo:

[http://www.xfree86.org/current/glxinfo.1.html](http://www.xfree86.org/current/glxinfo.1.html)

From there it looks like there's an option to change the display name.  Does that work for you?

Also, what does changing the display name do for you?

---

### Post by Toshick on 2007-12-17
no. I need to change display, where my gnome session is runnig.

---

