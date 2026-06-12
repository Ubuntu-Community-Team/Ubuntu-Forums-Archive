---
title: "Is the stock kernel built for G3 / G4 / or G5?"
date: 2008-03-27
forum: Apple PPC Users
---

### Post by stream303 on 2008-03-27
Is there a way to determine what build the stock Ubuntu PPC kernel is built for?

I'm not a compiler expert, and was wondering if the stock Ubuntu kernel is built for the lowest common denominator, ie a G3?

I'm running a G5 here, and wonder if the installer detects this and uses a different kernel, or can a G5 even run with a G3-built kernel, much like you can run a 686 on a 386 kernel?

If that's the case, then I guess I should go back over the notes here about building my own kernel specifically for a G5, especially if stock is for a G3...

Oops.  Guess I answered my own question by just doing a "uname -a" in the terminal, which shows ppc64.  Makes me wonder about the G4's, and if there would be any difference/benefit for a G4-specific compile?

---

### Post by BladeMelbourne on 2008-03-27
I believe that the ppc kernels (not ppc64) work on G3, G4 (7400) and G4 (7450) chips.

I believe there be some performance benefit compiling your own kernel.
This is probably also true for everything on the system (Firefox, etc) - GCC can make optimisations targeted at your chip (there is also altivec support to consider at this time too).

This probably applies to the intel crowd too. They might get their i686 or i586 kernel which works on older processors. They also get most of their packages as i386 - which would probably work on any pentium, and maybe backwards to the 386 chip.

It's been a long time since I looked into this. A Gentoo user would know for sure.

---

