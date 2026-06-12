---
title: "how often are drivers added to ubuntu?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by gino on 2007-11-01
Hi,
I just installed Ubuntu Gutsy on a HP Pavilion 2000. It works but two issues remain, graphis adapter seems to not allow compiz to work and the Webcam is dead. Now I have gone though the forums and tried this and that with no success and I am kind of fine with the fact that I can not fix the issues but I have a more general question. If the issues are that the right drivers do not exist, how often are drivers  updated? will they appear as an update in the update manager or should I be always googling for solutions? I mean the webcam and special effects do work in Vista so there is a way, I am not clever enough to make it happen but there are plenty fo hackers out there so I guess solutions will come...
Any comments suggestions welcome
Cheers
Gino

---

### Post by Crafty Kisses on 2007-11-01
> **gino said:**
> Hi,
I just installed Ubuntu Gutsy on a HP Pavilion 2000. It works but two issues remain, graphis adapter seems to not allow compiz to work and the Webcam is dead. Now I have gone though the forums and tried this and that with no success and I am kind of fine with the fact that I can not fix the issues but I have a more general question. If the issues are that the right drivers do not exist, how often are drivers  updated? will they appear as an update in the update manager or should I be always googling for solutions? I mean the webcam and special effects do work in Vista so there is a way, I am not clever enough to make it happen but there are plenty fo hackers out there so I guess solutions will come...
Any comments suggestions welcome
Cheers
Gino
You usually can download the drivers from the **Restricted Drivers Manager**. Just wait possibly a driver will be released.

---

### Post by macogw on 2007-11-01
First, do that ^

Drivers are in the kernel, so they're only updated when a new kernel is released (and usually only a few are updated if there's a bug to be fixed).  Compiling a new kernel that has that driver is the usual way.  It's not that scary.  I did it within 2 weeks of starting to use Linux.  If your graphics aren't supported now, though, they probably don't have open source drivers and aren't in the kernel anyway.  You likely need to get the driver from the card manufacturer's website.

---

### Post by kevdog on 2007-11-02
Compiling a kernel is technically easy (with help from a few guides), but learning how to do it properly takes a lot of skill and practice -- meaning exactly what to include in the vanilla kernel.  Its quite intimidating at first, and I still leave things out or compile too many modules I dont need!

---

### Post by macogw on 2007-11-02
> **kevdog said:**
> Compiling a kernel is technically easy (with help from a few guides), but learning how to do it properly takes a lot of skill and practice -- meaning exactly what to include in the vanilla kernel.  Its quite intimidating at first, and I still leave things out or compile too many modules I dont need!

Doesn't hurt to compile the whole thing *shrug* If you're a Gentoo ricer*, you'll disagree with that last statement.

*Ricer as in the people who mod their cars obsessively.  Gentoo users are known for tweaking the hell out of their installations to get top-performance...though they probably use up more time doing the tweaking than the tweaks save them.

---

