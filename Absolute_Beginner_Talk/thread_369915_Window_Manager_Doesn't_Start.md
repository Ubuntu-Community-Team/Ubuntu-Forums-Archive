---
title: "Window Manager Doesn't Start?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by mavigozler on 2007-02-25
I posted this a few days ago, probably in the wrong discussion group, since there was no reply.

My problem is that when the system starts up (in Gnome), after login, the large icon with "Ubuntu" logo and very small text saying "window manager" holds there for the longest time, and also a "terminal" application opens with shell prompt automatically, apparently as if I have a configuration problem or it's asking me to do something.

If I just leave it there, eventually the rest of the loading of the Gnome GUI continues.

But there are no windows!  I can open an application/task from the menu, but the "window" has no title bar with restore/minimize/maximize/close widgets, there is no resizing allowed at all, and no movement allowed at all.  There is no 'z' dimension either.  Clicking on a "window" that happens to show below the one above it does not bring that to the front as the active application.

I have since learned that the 'window manager' is indeed responsible for all the window behavior that is missing.

The question is, what caused a change in the system that would prevent the window manager from running, and how do I fix this, short of re-installing the entire system?

I believe that this occurred after I did a huge update of several packages, although I am not that sure, since I saw this problem the next morning, and it could result from more than just the updating of packages.

---

### Post by louis_nichols on 2007-02-25
Here's my thought: after you login, go to Applications>Accessories>Terminal. There, issue the command: ```
metacity --replace
```
This should fix things. After this, you can close the terminal window. The window borders will disappear again for a moment, but will appear again in a second.

---

### Post by mavigozler on 2007-03-02
Thanks, Louise

It worked, once I used the Package Manager to install metacity.  The libmetacity package was installed and present, but not the application.

---

