---
title: "apt locked?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by yurricane on 2007-03-30
hmm ok whenever i try apt-get and install sometimes it works and other times it comes up with this...

> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


Thanks in adv.

---

### Post by mac.ryan on 2007-03-30
To, me it looks like another process is locking the table already. Next time it happens, check if you left synaptic or system update or automatix or... open.

Just an idea, it might well be something else....

---

### Post by compiledkernel on 2007-03-31
Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

---

### Post by mac.ryan on 2007-04-01
> **compiledkernel said:**
> Automatix is unsupported software by the community. These forums do not support it either....

CompiledKernel, maybe you were trying to answer some other post? :confused:

The OP was asking about **apt**, not automatix...

---

