---
title: "More kernels than Iowa..."
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-04-24
I've got dual processors here, so I had to nab Linux 2.6.12-9-686-smp way back when I first started using Ubuntu.  Works great, no problems.

Thing is I've got Linux 2.6.12-9-386 and Linux 2.6.12-10-386 on the machine as well.  They're commented out in menu.lst - I did that, it wasn't automatic - and naturally don't appear among my boot choices in GRUB.  What I'm wondering is, can I be rid of those Linux images altogether, either by way of Synaptic or apt-bleh, or will something weird happen?

therunnyman

---

### Post by Parkotron on 2006-04-24
Just uninstall them with Synaptic. After the uninstall, the appropriate changes will be made to menu.lst automagically. No fuss whatsoever.

Personally, I like leaving the original "lowest common denominator" 386 kernel installed just as a fallback in case something should go wrong.

---

### Post by therunnyman on 2006-04-25
Excellent.  Thank you kindly.

That's a fine idea, leaving a backup kernel; I believe I'll do that.

therunnyman

---

