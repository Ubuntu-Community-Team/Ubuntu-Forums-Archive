---
title: "Desktop Effects no longer work after installing ATI drivers via Envy"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-08-29
I installed my radeon 9700 pro drivers via Envy and the Desktop Effects no longer work. :(

Any help?

---

### Post by Hork on 2007-08-29
Oh yeah!  This is the error I get:
The Composite extension is not available.

---

### Post by dstaudt on 2007-08-29
Unfortunately the proprietary ATI driver does not support AIGLX, which is needed by Desktop Effects.  The open source Radeon driver (which was probably installed by default) does, but of course likely not support all of the 3D features your card may have.  Sort of a catch-22.

It is possible to use XGL instead of AIGLX (there are several how-to's in the Customizations forum and elsewhere on the net,) which should  work with the proprietary ATI driver, but it's a somewhat problematic configuration (and XGL is not getting much/any development/bug-fixes going forward I believe.)

---

