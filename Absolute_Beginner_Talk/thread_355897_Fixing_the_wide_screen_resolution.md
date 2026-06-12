---
title: "Fixing the wide screen resolution"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by mekkah on 2007-02-07
I'm kinda new to Linux/Ubuntu, but i'm learning. And the resolution issue was a problem that almost made me go back to XP. But i remembered someone saying that "u gotta hang in there, it takes time to change operating system & feel comfortable about it". This is how i found a way to change my resolution from 1024x768 to my Easynote's 1280x800 without tampering with the xorg file:

* Use the Synaptic Package Manager to obtain a package called &#8221;**xresprobe**&#8221; (X Resolution Probe). Then reboot. It worked instantly for me. No fuss. 

I hope this will help out other ubuntu beginners to "hang in there" some more, since this is a really good linux distro.

Here's the description: 

X Resolution Probe
xresprobe is a package that probes both laptop and DDC-compliant screens for
their standard resolutions, and returns a specifically-formatted, easy-to-parse
output.

It contains the 'ddcprobe' package, which performs a DDC probe to the monitor;
however, ddcprobe only works on i386 and powerpc. The laptop detection routines
are, however, sufficiently generic to to be useful to other architectures.

---

### Post by ziggykg on 2007-02-08
Hey, thanks for this one.  I've often wondered if such a tool exists.
I have a 19" widescreen monitor and the tool would have come in handy when I setting it up.
Fortunately, my past experience of hacking xorg.conf files plus the monitor spec manual helped me through.

Thank you still.

---

