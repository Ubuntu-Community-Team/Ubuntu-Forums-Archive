---
title: "[SOLVED] ctrl shift esc equivalent"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by brett611 on 2008-02-11
What is the linux equivalent to windows ctrl+shift+esc that brings up active processes?  I've had a couple instances where an app locks the gui and the mouse clicks don't register.  in Windows ctrl shift esc would pop up the task manager and I could force the app to close.

thx

---

### Post by nikoPSK on 2008-02-11
> **brett611 said:**
> What is the linux equivalent to windows ctrl+shift+esc that brings up active processes?  I've had a couple instances where an app locks the gui and the mouse clicks don't register.  in Windows ctrl shift esc would pop up the task manager and I could force the app to close.

thx

there is System monitor, but I don't know the key combo... (System -> Administration -> System Monitor).

---

### Post by Dr Small on 2008-02-11
CTRL + ALT + BACKSPACE will restart X11 and take you back to the login screen.

---

### Post by brett611 on 2008-02-11
I don't want to close my current session, just the problematic application (typically amarok).  When it freezes I can't click any icons.  I have the session manager as an icon on the desktop and panel but neither works when this happens.  And I'm too stupid / lazy / stubborn to keep session manager open all the time

---

### Post by Dr Small on 2008-02-11
ALT + F2 will open the run dialog, then type "xkill" and click on the problematic application.

---

### Post by emarkd on 2008-02-11
How about <ctrl><alt>F1, log in and do:

```
 pkill amarok
```

Then <ctrl><alt>F7 will get you back to your GUI.

---

### Post by asmoore82 on 2008-02-11
no single application lock-up should cause the menubar and/or panel to stop functioning.
check the output of `dmesg` in a terminal("Applications->Accessories->Terminal")
immediately after a lock-up; just to make sure nothing else is going on:
```
dmesg
```

---

### Post by brett611 on 2008-02-13
Thanks Dr Small, emarkd, asmoore82.  I'll try all your suggestions as they are all valid, helpful and insightful.

Marking as solved.

---

### Post by nikoPSK on 2008-02-13
> **Dr Small said:**
> ALT + F2 will open the run dialog, then type "xkill" and click on the problematic application.
I learned about that a week ago. :)

---

