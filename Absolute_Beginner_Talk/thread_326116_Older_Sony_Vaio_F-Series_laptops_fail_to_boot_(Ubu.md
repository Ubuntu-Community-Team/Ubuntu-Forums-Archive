---
title: "Older Sony Vaio F-Series laptops fail to boot (Ubuntu 6.1 and Xubuntu 6.1 alternate)"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by lkvee on 2006-12-27
I define older F-series Vaios as those with the RAM sitting directly underneath the left side of the keyboard.  I had an F540 (P3/500) whose memory could be accessed by removing the memory slot cover instead of the keyboard.

I have a PCG-F350 (P2/366) and a PCG-F34 (Japanese/P2/400).   After some console activity, the laptops turn "off" - the power light's on, but there's no backlight and likely no image. On the F34, the fan goes off but kicks back in. I haven't checked the F350's fan.

When I booted the F34 with native Windows 98, Scandisk kicked in. The laptop froze with a blinking cursor in the upper-left corner afterwards.

I tried booting up with Xubuntu (Alternate) 6.1 and Ubuntu 6.1 on the F350. I tried Xubuntu (Alternate) 6.1 on the F34. Same dark LCD.

I'm planning to check both CD's and all laptop memory for defects.   Let's presume the media and memory check out OK.

Does sudden shutdown syndrome look like this?  I'm hoping there are Linux boot parameters that could provide a solution, even if it's only a band-aid.  I'll also look around for other accounts of Linux installations on either laptop.

Thanks for reading.

---

### Post by lkvee on 2007-01-01
I shut off APM and ACPI as well as adding the no-hlt parameter.  Seems to work so far.

Two URLs:

[http://www.physik.uni-freiburg.de/~zwerger/cip/Vaio/indexeng.htm](http://www.physik.uni-freiburg.de/~zwerger/cip/Vaio/indexeng.htm)
[http://www.physik.uni-freiburg.de/~zwerger/cip/Vaio/software-fix_Linux.htm](http://www.physik.uni-freiburg.de/~zwerger/cip/Vaio/software-fix_Linux.htm)

---

