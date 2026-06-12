---
title: "Startup from network signal"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by stijn_pol on 2007-01-13
Is there a way to startup a remote computer from let's say, receiving a network signal??
Thanks!
..perhaps not the right place to post, because this is a hardware issue?! isn't it?!

---

### Post by hal10000 on 2007-01-13
I hope I understand you well, you want to startup (boot ??????) a computer (Over network???) from a remote computer?

First, the computer which has to be started, needs a BIOS which has the wake-on-lan (WOL) functionality. (and of course you have to enable wol)
Then, on the other computer, presumed this is ubuntu or another linux you'll need one of the wakeonlan or etherwake packages.

---

### Post by stijn_pol on 2007-01-14
Exactly! 
Some more explanation: I'm testing with ubuntu server, but I don't won't the computer to be powered on all the time. Therefore I was wondering if i could do something like you just suggested since this testing server computer is not located nearby.
Thanks!

---

