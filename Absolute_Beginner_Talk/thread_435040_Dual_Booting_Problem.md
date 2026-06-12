---
title: "Dual Booting Problem"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Pedro.J.Cecil on 2007-05-06
This is the first time I've used any Linux distribution and, thus far, its going great. Everything works as it should and things are far easier than I thought.

But there is one problem, I still need to get into XP. Dual Booting works (as in, the menu to select which OS to boot into appears) but does not respond to my keyboard.
Its probably because my keyboard is wireless (and USB, by the way). 

Any solutions?

Thanks.

---

### Post by cotcot on 2007-05-06
Enable usb support in your bios. At least that is how I solved a comparable problem some time ago.

---

### Post by annda on 2007-05-06
because this happens before any OS boots, you will have to check your BIOS settings for USB support. i can't tell you where to look, since BIOS's are highly customized ans almost every model has a different one.

---

### Post by Pedro.J.Cecil on 2007-05-06
> **cotcot said:**
> Enable usb support in your bios. At least that is how I solved a comparable problem some time ago.

I'll have to get hold of a wired PS/2 keyboard first, so I can get into the BIOS... But I will try that when I can, thanks :popcorn:

---

### Post by Breff on 2007-05-07
I'm having the same problem.  What's interesting is that if XP is the last OS I've used then my USB keyboard works fine at boot-up so I can enter the BIOS and interact with the GRUB.  If UBUNTU is the last OS I've used, the keyboard can't be used until the OS loads.  Have a PS/2 keyboard to hand so will try the BIOS thing.  Will post the results.

Breff

---

### Post by Breff on 2007-05-07
Ok, this is strange.  I went into my BIOS and everything is enabled in the USB section.  So I don't think the problem (or the solution for that matter) is there.  But here's what's interesting: when I reset my computer as opposed to a cold reboot, the keyboard works again.  It's as if the reset makes the computer forget that UBUNTU was the last OS used.  I thought a cold reboot would have the same effect but no, only a reset.  Pedro, if you haven't yet got your hands on a PS/2 keyboard try the reset method and you might get control of the keyboard back.  It's a bit clumsy and not a solution per se but it might get you back into XP.

All that said, I'd like to find a more definitive solution.  What does UBUNTU change in the computer so that this happens??  What does a reset change on boot-up that a cold reboot doesn't??  I always thought that a cold reboot was much more definitive than a reset.

Anyone got any ideas?

Breff

---

### Post by kakalaky on 2007-05-07
You need to enable usb legacy support in the bios.  Sometimes this setting is not with the rest of the usb settings in the bios, so you might need to look around for it.

---

### Post by Breff on 2007-05-07
I tried that but it didn't make any difference.  Thanks anyway. Might work for Pedro though.  I'd be interested to see.

---

