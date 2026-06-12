---
title: "Disabling touchpad + other touchpad goodness"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by jkblacker on 2007-05-04
Hi,
I normally use a usb mouse with my laptop, which is working fine - perfectly, in fact. A couple of questions/points I'd like clarified if you could:

1) Is disabling my touchpad as simple as commenting out the relevant entry in xorg.conf? I've seen it in there, but is this the only thing that needs to be changed?

2) Is it possible to change the sensitivity of the touchpad? I find that under Ubuntu it seems to be a lot more sensitive to a gentle touch than under XP.

3) My mouse is a usb mouse which gets recognised automatically. In XP I can disable the touchpad automatically when the mouse is present - how do I achieve the same under Ubuntu?

P.S - I'm running Feisty if that will make any difference!

Many thanks!
Josh

---

### Post by Slackpacker on 2007-05-04
get gsynaptics (aka Touchpad) in Add/Remove.  You will need to edit xorg.conf to add the line "Option"   "SHMConfig"   "true" in the synaptics touchpad section.

---

### Post by jkblacker on 2007-05-04
Thanks for that!

Was I right about commenting out the touchpad option in xorg.conf do you know? I would just try it but am wary of editing that file willy-nilly!

EDIT: Sorry, I was being completely stupid and missing the 'Disable touchpad' option...duh!

---

