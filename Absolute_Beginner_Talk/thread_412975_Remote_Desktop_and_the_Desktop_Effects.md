---
title: "Remote Desktop and the Desktop Effects"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Forcepath on 2007-04-18
I'm not sure if this is beginner talk, but I'm rather new here, I've been using Feisty Fawn for 3 days now (loving it!), but I've come across a bit of a problem.

I love the eyecandy of using the visual effects, it really grabs me in terms of prettyness without interfering with functionality, but it seems when I enable the visual effects, I am unable to do ANYTHING in a remote desktop session from Windows to Ubuntu.  I'm in a 100gb ethernet environment, and I have successfully used remote desktop earlier in the day before enabling desktop effects, and now when I connect to my Ubuntu desktop it loads and then I'm unable to interact with the desktop visually, but anything I've accidentally done/clicked through the VNC connection shows up if I disconnect completely from the session and reconnect to it. 

Is this a bug or am I going to have to turn off visual effects to use a remote desktop solution?

---

### Post by wormser on 2007-04-18
I use remote desktop going to a Mac.  In order for it to work well I had to turn down the display colors from millions to thousands.  Basically you are trying to pull too much data from the remote desktop and your connection cannot handle it.  So, it is not a bug.

Just turn off visual effects.

---

### Post by Forcepath on 2007-04-18
> **wormser said:**
> I use remote desktop going to a Mac.  In order for it to work well I had to turn down the display colors from millions to thousands.  Basically you are trying to pull too much data from the remote desktop and your connection cannot handle it.  So, it is not a bug.

Just turn off visual effects.

*cries*

But...but...so pretty!  I guess if this is the solution, I can deal, I was just hoping that maybe there would be a different option.

---

### Post by kungfoofool on 2007-04-25
I have been having the same problem.

There is a bug filed here:

[https://bugs.launchpad.net/vino/+bug/77442](https://bugs.launchpad.net/vino/+bug/77442)

---

