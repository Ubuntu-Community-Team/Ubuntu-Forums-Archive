---
title: "[SOLVED] Frostwire: Cursor has wrong focus"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by laidback on 2007-08-19
I've installed Frostwire via Synaptic onto my Feisty Fawn, it does work but...when you start it up the cursor is always on the Chat Room tab regardless of whether chat room is enabled or not. The effect of this is that you cannot enter anything into the Search tab without first messing about with the Chat room tab in order to move the cursor focus onto the Search tab. It's just annoying as it can also happen later on although then the sequence of events that triggers it is a little bit more difficult to determine. 

Any ideas as to the cause and solution of this would be most welcome. It happens on both my desktop pc and laptop so I doubt that it's a keyboard problem.

Kindest Regards

Laidback

---

### Post by laidback on 2007-08-21
See here for work around:-

[http://ubuntuforums.org/showthread.php?t=529639](http://ubuntuforums.org/showthread.php?t=529639)

---

### Post by dacha on 2007-12-29
Solved? I think not yet :). Here's what you do:

(I'm using the tarball, if you used the .DEB figure it out)

Edit runFrostwire.sh and change
*export AWT_TOOLKIT=MToolkit*
to
*#export AWT_TOOLKIT=MToolkit*

Why they are using MToolkit (Motif toolkit) instead of XToolkit is beyond me...

---

