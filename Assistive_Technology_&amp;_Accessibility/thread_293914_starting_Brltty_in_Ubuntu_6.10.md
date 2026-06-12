---
title: "starting Brltty in Ubuntu 6.10"
date: 2006-11-05
forum: Assistive Technology &amp; Accessibility
---

### Post by Pipistrelle on 2006-11-05
Hi. I can't get my braille Lite 40 to work with Brltty. I try this from the command line:

sudo brltty -b bl

and this from the boot prompt:

linux brlttty=bl

In the first instance, I get a version number for Brltty and the message "screen driver for Linux". I get no results with the second method. Is there anything else I can do or change?

Thanks,
Teresa

---

### Post by Pipistrelle on 2006-11-07
Hmmm, I'm going to post this in case anyone else has the same adventures I have had for the past few days.

I've found out that ttyS0 (the serial port) is no longer a default. Thus:

Boot prompt:
linux brltty=bl,ttyS0

or

command line:
sudo brltty -b bl -d ttyS0

Yay! :)

Teresa

---

### Post by frafu on 2006-11-08
Thanks for letting us know.

frafu

---

### Post by Henrik on 2006-11-10
Hi Teresa,

We have plans for improving brltty support for Ubuntu 7.04. I'd appreciate your vfeedback on this specification: [https://wiki.ubuntu.com/Accessibility/Specs/BrailleSupport](https://wiki.ubuntu.com/Accessibility/Specs/BrailleSupport)

That is intended to make use on both the Live CD and installed systems easier.

---

### Post by Pipistrelle on 2006-11-16
Yes, the Braille accessibility roadmap looks great. I wish I were a bit more knowledgeable about how these things are implemented, but I do know that the Kudzu demon causes problems when probing. I very much like the idea for an item in the f5 accessibility menu.

Thanks,
Teresa

---

