---
title: "nvidia / GLX crashes X (but only when invoked)"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by gnoel on 2007-04-07
I installed the nvidia driver with GLX support after much trouble and everything was working fine.  I was using a nice 3D screensaver, was enjoying Google Earth, and playing Tuxracer.  It was Linux bliss for over a week, until ...

... yesterday, I wanted to show my spouse the wonder that is Google Earth and when I started it up, the Google Earth splash screen appeared briefly and then xserver crashed.  Next thing I know, I'm hearing the bongo beat and logging into the GUI again.

I didn't change anything in the meantime - I think I was only using the command prompt to find files.  I can't recall anything crashing hard during that time.  Now, X crashes whenever any one of these events occurs:

- start any app or game that uses GLX
- try to display the GLX status in the "Nvidia X Server Settings" GUI
- try to access System/Preferences/Screensaver (since the previously selected screensaver was 3D)

It's the screensaver problem that is hurting me - otherwise, it's not much worse than the old nv driver.  However, if I leave my computer for more than 10 minutes and the screensaver tries to activate, my desktop crashes.  Questions:

1) What is wrong with GLX and how do I fix it?
2) Or at the very least, how do I disable the screensaver from the command line?

Thanks in advance!

---

### Post by fordfan753 on 2007-04-07
Try this possible fix

[HTML]http://ubuntuforums.org/showthread.php?t=403164&highlight=nvidia[/HTML]

---

### Post by alienexplorers on 2007-04-07
I had the same problem last night.  Opengl graphics were working correctly and after a restart the GLX portion of my nvidia drivers was toast..Ended up running the envy script and uninstalling the nvidia drivers.  Then I ran it again and reloaded the nvidia drivers.  After a cold start everything was back to normal... Really Weird???

---

### Post by gnoel on 2007-04-07
Cool - the other thread worked.  Thanks fordfan753 for the right answer.  Next time I'll look harder in the forum.  :) 

Note to alienexplorers: Good that Envy worked for you.  Envy didn't do so well for me - the driver it loaded was incompatible with the kernel, so I made a fresh one from the nvidia site.  Maybe this was because I was installing an older version of the driver (for my geforce3 card).

---

