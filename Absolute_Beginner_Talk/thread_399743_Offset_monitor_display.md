---
title: "Offset monitor display"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2007-04-02
I have a desktop with ubuntu and xp.  When I am on the XP machine the monitor is fine, when I switch to the ubuntu machine the display is slightly skewed to the right.  I move the display over with monitor controls but that messes it up when I go back to XP.  I am using a KVM, but I'm reasonably sure the problem is independent of the device as it occurs when I remove the KVM from the equation.  Is there a way to fix this problem?  The ubuntu desktop appears as if a small part of it is just off screen.

---

### Post by bulldog on 2007-04-02
I know what you mean,had the same issue.
If possible connect the monitor with the DVI connector and it should be fine.

Don't know if there's another solution,I didn't look for it,I just pressed the auto-correction button.

---

### Post by RedSquirrel on 2007-04-02
The auto-correction should work. Sometimes it helps to setup a Modeline in /etc/X11/xorg.conf if you know the refresh rate for the resolution you want to use with your monitor. 

[Here]("http://ubuntuforums.org/showthread.php?p=454217") is a guide to help with that.

---

