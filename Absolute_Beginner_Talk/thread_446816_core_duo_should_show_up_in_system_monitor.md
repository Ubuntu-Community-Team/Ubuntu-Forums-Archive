---
title: "core duo should show up in system monitor?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-05-17
I think my core duo isnt working.  I have feisty installed.  The 2nd core shows up in breezy but not in feisty.  Is there anything I can do?

---

### Post by Cypher on 2007-05-17
Open up a terminal Applications->Accessories->Terminal and show us the output of
```

uname -a

```
If you don't see SMP in that output, then you're not running the SMP kernel and won't make use of the 2nd Core.

---

### Post by outer_space on 2007-05-17
Linux josh-laptop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

In synaptic it says linux-SMP module has been replaced by linux-image-generic, maybe thats the problem.

---

### Post by EndPerform on 2007-05-17
> **outer_space said:**
> Linux josh-laptop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

In synaptic it says linux-SMP module has been replaced by linux-image-generic, maybe thats the problem.

Exactly.  Install the generic kernel, and reboot.  When you install it, it should become the default kernel.  Give that a try and see if it helps.

---

### Post by outer_space on 2007-05-17
Yes!  The generic kernal enables the second core.  Thanks.

---

