---
title: "syslog entry - APIC error on CPU0"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by 1952mudflap on 2007-03-04
Mar  4 07:39:15 ronm-desktop kernel: [17218638.156000] APIC error on CPU0: 40(40)

I don't normally mess around in this area yet, (still a lot to learn) but I was referred to the syslog for more information when I was trying to mount a network drive for amarok use.  When I looked, I found the above entry at least a "zillion" times, which concerns me a bit.  Is this a problem that I should be resolving or is this something normal?

Any help would be appreciated since I'm a real noob at this. By the way, I'm using Kubuntu but there seems to be a greater likelihood of a response on this forum!

---

### Post by 1952mudflap on 2007-03-04
If anyone should by chance read this thread, I did happen to find a bug (below) that indicated that this error often happens with the use of OpenGL screensavers.  Sure enough, I'm using one and usually, when I come back after it's been on for a while, the screensaver is locked up. Never thought much of that, it hasn't affected the performance of my computer or Kubuntu so I blew it off.
I will now disable the screensaver and see if the error goes away.



[http://bugzilla.kernel.org/show_bug.cgi?id=6404](http://bugzilla.kernel.org/show_bug.cgi?id=6404)


I frequently ask myself why I post in forums, since it's usually like talking to yourself and I DON'T do that !

---

### Post by 1952mudflap on 2007-03-04
I changed the screen saver from an OpenGL one to a blank screen and in 1 hour I had 4 instances of the (40)(40) error, so unless it's screen savers in general, I doubt that this is the cause.

---

### Post by 1952mudflap on 2007-03-04
Interestingly, at 9:48 am I turned off the screen saver all together and it is now 7:34pm and I haven't had a single instance of this "APIC error on CPU0 (40)(40)" since I turned it off.

I guess that speaks for itself.

Hope somebody finds this useful.

---

