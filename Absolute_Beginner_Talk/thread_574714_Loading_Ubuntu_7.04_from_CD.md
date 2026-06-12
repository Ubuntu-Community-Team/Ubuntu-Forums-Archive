---
title: "Loading Ubuntu 7.04 from CD"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by philferrar on 2007-10-13
I've just obtained a copy of Ubuntu 7.04 "Starter Kit" from Computer Active magazine. After the initial splash screen has been running for a few seconds the screen blanks out and a couple of lines starting "Busybox ..... " appear at the top of the screen quoiting version numbers etc.
 This is followed by something like ...
 /bin/sh:   can't access tty; job control t????d.fs  [sorry about the ???? - can't read the note I scribbled down !]
(initramfs)
 At this point it just sits and does nothing.
 My laptop is a Samsung V20 with 512Meg of memory - any idea why it's failing to load properly?

---

### Post by banewman on 2007-10-13
Some laptops have trouble - when the cd starts to boot and the screen says " start or install ubuntu" press F6 and at the end of the line that comes up type a space then -    noapic nolapic   -     most times that is the solution. :)

---

### Post by philferrar on 2007-10-15
Hi, thanks for responding but it didn't work [unless I got it wrong] - I pressed F6 then when the line at the bottom appeared I entered " noapic nolapic   " [leading space  without the quotes, or the "-"'s in your original text. Have been advised to wait for 7.10 later this week before going further but it might be a general kernel problem for some laptops.

---

