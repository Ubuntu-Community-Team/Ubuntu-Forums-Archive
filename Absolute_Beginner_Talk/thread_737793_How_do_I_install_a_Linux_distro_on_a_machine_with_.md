---
title: "How do I install a Linux distro on a machine with no CDROM or USB?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-03-27
What I have is a REALLY old laptop. I'm not ready to use it as a doorstop yet, because it's in incredible condition.

Specs:
Pentium I @ 75MHz
2-4GB HDD (unsure precisely...I haven't taken the 10 seconds to pop it out and look)
32 MB RAM
No OS currently installed
No CDROM, no USB...floppy only!

I've been scouring various sites trying to find a floppy-based distro, but I haven't had any success. I tried "BasicLinux," but it spewed error codes at me when I booted with it, so no dice there.

I could get Windows 95 on it, so surely there's a Linux alternative...right? I really don't want to have to go the Windows route.

Any ideas? I know this may not be the IDEAL forum for this because there's no way I'll get a 'buntu to run on this beast, but the people here have always been very helpful and kind to me, even when my questions are completely off-topic (like this one).

Thank you in advance!

EDIT: To complicate matters, I have no external drive I could plug in, and no other laptop into which I could transplant a HDD for install that way.

---

### Post by Joeb454 on 2008-03-27
It looks like you'll need floppy based installers...Though I don't know of any distro's which come with that as an option :)

---

### Post by llamakc on 2008-03-27
What about an older Debian netinstall?

---

### Post by aktiwers on 2008-03-27
I was gonna suggest debian netinstall too..  did it on an old laptop too and it works great.
Edit: Actually doesn't Ubuntu have a netinstall too?

---

### Post by doctorbighands on 2008-03-27
(researching Debian Netinstall...)

...any tips on this from your own personal experiences?

---

### Post by doctorbighands on 2008-03-27
Would I be able to use a PCMCIA wireless card for this?

---

### Post by NullHead on 2008-03-27
> **doctorbighands said:**
> Would I be able to use a PCMCIA wireless card for this?

Wifi tend to have issues with drivers so I'd use an ethernet cable and adapter.

---

### Post by Hospadar on 2008-03-27
I think it's actually not possible to do a debian netinstall with a wifi card, so you'd have to use ethernet (pci i'd assume since it sounds like there's no built-in)

Probably though, even a totally clean ubuntu or debian install is too heavy for this machine.  You may want to see if it's possible to netinstall damn small linux, or maybe netinstall debian with absolutely no gui and install your own window manager (fluxbox or jwm) on top of that.

---

### Post by tubasoldier on 2008-03-27
I did a Debian floppy net install on my old old old laptop. it works rather well. The default install is suprisingly similar to Ubuntu's. I think it requires around 3 floppies?

And as long as your PCMCIA wireless card is supported then of course you can use it. I have a cisco aeronet PCMCIA wireless card that works great.

Good Luck.

---

### Post by Forrest Gumpp on 2008-03-28
@doctorbighands

This link may be of some help:  [http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

I got it from this Google search:  "Linux distro on floppies".  I only looked at the first site listed.  There may be better info further in.



PS  I didn't use quotation marks in the actual search field on the Google page.

---

### Post by theRightNee on 2008-03-28
yeah, i think you're best of with some of the super small distros damn small and puppy linux, both of which (i believe) can be installed from a floppy. i know there is a thread around here somewhere with a list of some of the smallest distros (they number under 3 MB)....and i'll post it if i see it =]

---

