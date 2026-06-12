---
title: "Mouse button mapping"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-04-13
So far so good. First, thanks for all of the help I have gotten so far, either from the questions that I asked or from cruising the threads. 

I have a Logitech MX laser mouse, and so far have gotten all of the buttons to respond. Most of them do what I want, but I would like to map the button that comes up as button 13 in xev to be a control-w. At the moment, it acts as a back button, but so does another one. What would be the place to put it and the syntax? I think that If I can get this one, I can figure out the others if I decide to change any of them.

Followed the tutorial balow and finally figured it out. It did take me awhile to determine the exact syntax needed.

---

### Post by chalex on 2007-04-14
I think the mouse section of your /etc/X11/xorg.conf has something to do with this.

---

### Post by freakavoid on 2007-04-14
There can be other ways but the solution I'm currently using for this problem is: have the mouse button run a command trough xbindkeys and send the desired key combination to X using xvkbd virtual keyboard in this command. This should work assuming the mouse button is already recognized by the system. Take a look at the section 2 in [this]("http://ubuntuforums.org/showthread.php?t=219894") Howto.

---

### Post by igknighted on 2007-04-14
> **freakavoid said:**
> There can be other ways but the solution I'm currently using for this problem is: have the mouse button run a command trough xbindkeys and send the desired key combination to X using xvkbd virtual keyboard in this command. This should work assuming the mouse button is already recognized by the system. Take a look at the section 2 in [this]("http://ubuntuforums.org/showthread.php?t=219894") Howto.

Use that whole tutorial.  Evdev is a great driver, I have no idea why Ubuntu refuses to use it by default.  It will make your life very easy when using xkeybind/xvkbd to enable mouse shortcuts.

---

### Post by dondad on 2007-04-15
Thanks. I used the tutorial and finally got it working. It took me awhile to figure out the exact syntax for the xbindkeysrc entries, but now it is working. Appreciate all of the help.

---

