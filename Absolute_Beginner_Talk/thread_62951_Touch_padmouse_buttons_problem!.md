---
title: "Touch pad/mouse buttons problem!"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by nixie21 on 2005-09-06
Hi, new to UbuntU and linux in general.  Install went fine but from time to time the touch pad and mouse buttons stop working, the cursor just freezes and I need to shutdown and restart the system...  The keyboard works and I can work in a terminal to shut down (not sure of the command for a full shutdown!?)

It is a p3 1gig dell laptop, 256m ram...

I am not sure of where to look at log files or what to even look for, but I found this:

Sep 5 19:55:06 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
Sep 5 19:55:06 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Sep 5 19:55:06 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Sep 5 19:55:06 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.

sometimes the last line says - instead of the resynched line (trying to remember - something like)

last line repeated 80 times
last line repeated 800 times...

Thanks for any input and help!!  THese forums are great!

---

