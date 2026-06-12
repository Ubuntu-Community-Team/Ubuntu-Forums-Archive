---
title: "[SOLVED] How much Ram am I using?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by u-slayer on 2007-09-11
How do I know how much ram I am using?

The System Monitor says that I am using  240 of 1002 megabytes.

Yet, the command $free -m says

             total       used       free     shared    buffers     cached
Mem:          1002        921         80          0         76        504
-/+ buffers/cache:        340        661
Swap:           63          2         61


Which one is correct? Will buying more ram make my comp run faster?

---

### Post by pinoyskull on 2007-09-11
if you are talking about physical ram, type

```
cat /proc/meminfo |grep MemTotal
```

---

### Post by u-slayer on 2007-09-11
Thanks, but that says the exact same thing as $free -m

by the way, WTF is dirty ram?

---

### Post by bodhi.zazen on 2007-09-11
Unused RAM is wasted RAM :)

This is different the Windows :twisted:

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by u-slayer on 2007-09-11
> **bodhi.zazen said:**
> Unused RAM is wasted RAM :)

This is different the Windows :twisted:

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)


Thank you! That answered all my questions. I have been wondering about this for some time now.:)

---

