---
title: "PPC - Powernowd Fix works great!"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-08
Well, the switch back to powernowd seems to be permanent for me now.  Thanks to this:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

and the section on how to fix cpu-frequency scaling.  The fix doesn't appear in the list of contents, but the fix is about half-way down the page.

With that fix, powernowd is more valuable than before.  I just put the cpu-frequency scaling applet in the top panel, and lo and behold, it is totally user-customizable without having to run it suid like before.

Normally I used to run CPUDYN instead of powernowd since it had only two states and cut down on the latency when I was doing intensive stuff in Gimp, etc.  Now, with the powernowd fix, I just click on the applet and can choose what I want when I want.  Nice!!

I'm not sure if this is Intrepid-specific, or if it also works in 8.04 Hardy, as I wiped out my Hardy install.

Might be worth looking into if you desire less latency at times, yet still want powernowd features in your ppc box.

---

### Post by stream303 on 2008-11-09
I may have spoken too soon about powernowd. :)

While the additional configurability seems nice, for some reason I'm not sure it is keeping my selection.  I guess I could start looking to edit the powernowd config file, but I'm back to using CPUDYN for the time being.

One thing is for sure - when measured at the wall outlet, the power saving on this desktop Apple box does indeed save about 10 watts at half-speed when it goes into power saving mode.

---

