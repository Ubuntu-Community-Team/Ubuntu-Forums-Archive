---
title: "Possible Ubuntu bug?  Or did I screw them up"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Fred_G on 2007-05-05
I have had searched around, but not found much on my problem.  I have a Ubuntu 6.06? folding box that has been locking up about every hour or so.  The only thing I can do is hit reset, even the keyboard num lock does not work.  I swapped out the PSU, same problem, then I noticed I can play games, browse the web, and use it for hours with no problems.  I disabled the screen saver and it has been folding for 3 hours or so, and no crash.

I have another folding box on Ubuntu 5.1, and it is behaving the same, except I can get a screen and mouse, but can do nothing but move the mouse around.  All the parts of the toolbar are not there except the bar.

Both of these boxes have an Abit NF7-s mobo and the first has an ATI 9800XT video card, and the other has an ATI 9250 video card.

I ask out of curiosity.  I am trying to learn how to use Linux.  If disabling the screen saver fixes it, I am good with that.  These are just Folding @ Home computers that I play around with trying to learn.

I had the computer with the ATI9250 running Fedora C5 for around a year with no issues, so I am curious as to what is up.

Thanks for your time.

E

---

### Post by gradedcheese on 2007-05-05
yeah, sounds like an issue with the ATI driver (do you know which one you're using)?  Perhaps it crashes only when a 3D-accelerated screensaver gets chosen?

---

### Post by alienexplorers on 2007-05-05
I had a similar problem with my old ATI card.  It caused a reset of my system every time it ran any Opengl graphics.  Updating the driver cured the problem.

---

### Post by Fred_G on 2007-05-05
Thanks for the info.  As far as the driver, they are running whatever Ubuntu gave them, and I have no clue as to how to update them.

Both are still doing their jobs with the screen saver disabled.  I can live with that, but would like to fix it for the experience.

Again, thanks for your time.

E

---

### Post by freebird54 on 2007-05-05
I haven't found a fix yet, I just avoid certain screensavers.  Any of the 'slideshow' type are safe enough (Cosmos for example) bu the 3d ones seem to hit a limit somewhere.  I find this strange as the same card/driver combos can run the 3d eye candly (Beryl) without locking up....

---

### Post by Fred_G on 2007-05-05
Thanks for the info freebird.  Seemed odd for me to blame a crash on a screensaver!  But both have been up and working for hours now with no problems.  Heck, when I am done with them, I turn the monitor off anyway, so no big deal.  I was beginning to think I was crazy blaming an OS for a crash.  I am used to working/trouble shooting windows machines.

E

---

### Post by freebird54 on 2007-05-05
Well - I have had the same thing with Windows too - but in an earlier incarnation :)  I think it was a third party screensaver too, so I can't blame MS for it....

We'll just have to hope that AMD/ATI will get around to proper Linux drivers sometime soon - at least they DO have something for us!

---

### Post by gradedcheese on 2007-05-06
> 
We'll just have to hope that AMD/ATI will get around to proper Linux drivers sometime soon - at least they DO have something for us!


It's actually the opposite: if they just released a little documentation on their damn chips, the community would write high quality drivers for them that would never cause crashes.  Instead, they release binary-only (closed) drivers with tons of bugs and refuse to provide any documentation.  So open-source drivers for ATI (NVidia too) are written via a painful reverse-engineering process that takes a long time.  

Trust me, you don't want them developing this junk further.  You want them to release documentation so that the kernel community can provide maintainable and quality drivers.  Look at Intel video support for an example of how it could be...

---

### Post by freebird54 on 2007-05-06
Well - yeah.  I am aware of that alternative.  I suspect, though, that even *IF* they do release sufficient documentation, it will be for 'older' chipsets - which wil be great for those with 'legacy' cards, but not so much for those with the latest/greatest...

As it is, I am amazed with the abilities of the 'radeon' open source driver I'm running on my Feisty.  Yes - the solution would be docs - but the amount it would 'give away' about the hardware is a problem IMHO.

---

### Post by gradedcheese on 2007-05-06
> but the amount it would 'give away' about the hardware is a problem IMHO

I don't think I agree... in my experience (I've written several drivers), the really critical stuff that a company wants to keep secret always happens inside the chipset itself.  The driver doesn't do anything amazing that a competitor would benefit from knowing, all the 'magic' happens inside the hardware.  All they need to document is the device-to-OS protocol, so to speak.  The kernel hackers don't really care how their amazing little chip works, they just want to set some bits and move data into the right place, essentially.  

This is also why these damn cards' drivers can be reverse-engineered with enough work.  You spy on enough driver->hardware traffic, and you can figure out what bits get set and why and where data gets written and when.  You won't learn anything about the proprietary hardware that way, but it's not like you were trying to.  In fact, if you know some C, take a look at that Radeon driver you mentioned and see if it looks like it gives any secrets away ;)

---

### Post by freebird54 on 2007-05-06
It won't reveal any secrets to me :)  I have done some work in C, but never any driver level stuff.  For that, all my experience is in 680x0 assembler (blast from the past) or even a bit of 6502/6510 assembler (further in the past!).

I was just trying to cut them some slack - but I guess my scissors were too dull....

I still have HOPE that AMD ownership will change things a bit - but we have to wait and see for a while yet (sigh)

---

