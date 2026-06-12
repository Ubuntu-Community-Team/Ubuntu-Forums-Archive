---
title: "Respawning error when booting LiveCD"
date: 2006-08-24
forum: Apple PPC Users
---

### Post by Org on 2006-08-24
Hi guys & gals,

When booting with Dapper Drake LiveCD on my laptop, boot-up process hangs at the following step:

```
Decompressing Linux... Ok, booting the kernel.
kill: Could not kill pid '3686': No such process
 * INIT: Id "2" respawning too fast: disabled for 5 minutes
 * INIT: Id "3" respawning too fast: disabled for 5 minutes
 * INIT: Id "4" respawning too fast: disabled for 5 minutes
 * INIT: Id "5" respawning too fast: disabled for 5 minutes
 * INIT: Id "1" respawning too fast: disabled for 5 minutes
 * INIT: Id "6" respawning too fast: disabled for 5 minutes
 * INIT: no more processes left in this runlevel
 * INIT: Id "3" respawning too fast: disabled for 5 minutes
 * INIT: Id "5" respawning too fast: disabled for 5 minutes
 * INIT: Id "6" respawning too fast: disabled for 5 minutes
 * INIT: Id "1" respawning too fast: disabled for 5 minutes
 * INIT: Id "4" respawning too fast: disabled for 5 minutes
 * INIT: Id "2" respawning too fast: disabled for 5 minutes
 * INIT: Id "1" respawning too fast: disabled for 5 minutes
 * INIT: Id "3" respawning too fast: disabled for 5 minutes
 * INIT: Id "4" respawning too fast: disabled for 5 minutes
 * INIT: Id "5" respawning too fast: disabled for 5 minutes
 * INIT: Id "2" respawning too fast: disabled for 5 minutes
 * INIT: Id "6" respawning too fast: disabled for 5 minutes
_
```

Here are my laptop machine specs:
[LIST][*]Intel Pentium 4 CPU 2.40 GHz
[*]768 Mo RAM
[*]NVIDIA GeForce4 440 Go 64M[/LIST]

Do you have any idea of what should I do to get it to boot up properly?

Thanks in advance for any suggestions.

-- 
Org

---

### Post by Pocket Aces on 2006-08-27
I am having the same problem.  I just bought a new IBM (Lenovo) Z60m thinkpad planning to put Ubuntu on it.  Can't even load the liveCD, thats not good.  Any help to this issue would be greatly appreciated.  (Downloaded the latest official/stable build today from ubuntu.com)

---

### Post by voxel on 2006-08-28
I already replied to Pocket Aces post... But I am also having the same problem :confused:

Any help/suggestions would be greatly appreciated!

---

### Post by Keywil on 2006-09-07
Hey all, Just purchased a new Dell and am ditching the XP for a Linux flavour.  anyhoo... 

I had the same problem, so did a <control><alt><delete> and rebooted from the CD a second time.  The second time worked like a charm.

Perhaps try rebooting from the cd again if it hangs.

---

