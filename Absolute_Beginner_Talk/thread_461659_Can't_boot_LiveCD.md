---
title: "Can't boot LiveCD"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by tll_2k on 2007-06-01
Ok. I tried booting from the live CD on an older HP desktop. I've installed ubuntu onto my wife's hp laptop using the same disk, so I know the disk burned right. The desktop has a Pentium 4, so the X86 disk is the right one to use, right? It boots to the menu with "Start or install ubuntu", "Start in safe graphics mode", "memory test", etc. So I pick start. then, it says : loading linux kernel, and after it loads, I get a black screen with a blinking cursor and this at the bottom of the screen:

```
Int 14: CR2 df800000  err 00000000  EIP c020c384  CS 00000060  flags 00010007
Stack: c00f8050 c03f129b c0371d8c 00000002 c00f8059 000f8050 00000000 00000000
```

I've tried adding the boot options noapic nolapic, and they didn't do anything different. I've tried safe graphics mode, and the same thing. Should I just use the alternate CD or is there something else to try?

---

### Post by hellmet on 2007-06-01
Similar threads with people having similar problems.

[http://ubuntuforums.org/showthread.php?p=2759447](http://ubuntuforums.org/showthread.php?p=2759447)
[http://ubuntuforums.org/showthread.php?t=402536](http://ubuntuforums.org/showthread.php?t=402536)

I guess its now a BUG too.

---

