---
title: "Google Earth Locks Up in Feisty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Apollo17 on 2007-04-24
Hey there,

I upgraded to Feisty last night. Works great, but Google Earth locks up the PC completely a few seconds into it's zooming down on the Earth after I type a location. The program Celestia does the same thing.

I figure it may be a video card issue (seems a lot of problems with Ubuntu are video related, especially to ATI cards. Unfortunately in this old Athlon 900 Mhz PC I'm using as a test bed for Ubuntu, I have an ATI Rage Fury Pro card, and I suspect that is causing the lock ups.

After a Google search I located a review of Google Earth for Ubuntu that read in part:

"You can, however, run into trouble with either using an older version of the glibc library or with a case of the drivers for either ATI or NVIDIA 3D graphics cards conflicting with glibc's pthread. The quick and dirty fix, in any of these cases, is to export the environment variable LD_ASSUME_KERNEL=2.4.10 to the system before running Google Earth.

A better approach would be to upgrade your graphic card drivers, and make sure that you're running glibc 2.3.5 (or later) with NPTL (Native POSIX Thread Library) support."

Would anyone be so kind to explain to this newbie, first, how to "export the environment variable" as shown above to the system? I have no idea what he is talking about. Secondly, I assume I'm running a generic ATI video driver as installed by Ubuntu, but is there a "better" one available for downloading from ATI?

Finally, how do I make sure I'm running glibc 2.3.5 (or later) with NPTL support?

Sorry for all the questions, but Google Earth is awesome and I'd love to be able to use it on this Ubuntu PC.

If I keep having problems related to the video card and/or drivers, would someone recommend a decent low end Nvidia based card I could replace the ATI with. I know there are "screamers" out there costing many hundreds of dollars, but I can't justify a card like that for this old PC. And how hard is it to get Ubuntu to recognize a new video card?

Many thanks,

Ross

---

