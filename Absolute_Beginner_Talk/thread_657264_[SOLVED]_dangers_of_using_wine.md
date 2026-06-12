---
title: "[SOLVED] dangers of using wine?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2008-01-03
are there any?  linux isn't in danger of windoze viruses, but what if a program is rigged to erase a file or something.  could it damage my linux files?

---

### Post by Dr Small on 2008-01-03
It may ruin the wine files, but it can't infect your system. If it does ruin wine, then just remove it and reinstall it.

---

### Post by hyper_ch on 2008-01-03
not really... there was  a test with some windozw viruses... I think you can find it on digg.com

---

### Post by FuturePilot on 2008-01-03
The worst it could do is hose your .wine directory. That's all. It can't harm the Linux system.

---

### Post by Niklas Schröder on 2008-01-03
sweet.  that's what i thought.  just wanted some reassurance before i started my project.  :p  thanks!

---

### Post by ubuntu27 on 2008-01-03
Some reading to do:

Experiment: [Running Windows viruses with Wine]("http://www.linux.com/articles/42031")

[What would happen if you ran a windows virus using Wine]("http://ubuntuforums.org/showthread.php?t=72598")

---

### Post by dr.silly on 2008-01-03
article is hilarious

---

### Post by philinux on 2008-01-03
Only thing I would add is that from reading posts on here I would stick to the version of wine in synaptic.

---

### Post by The Cog on 2008-01-03
> **FuturePilot said:**
> The worst it could do is hose your .wine directory. That's all. It can't harm the Linux system.

Not necessarily true. Check with the program winecfg, but the default is to map Z: to / which makes the whole Linux filesystem visible, and any user writeable files could be damaged.

I don't think wine is good enough to suport viruses yet, but trojan programs might find drive Z very interesting.

---

### Post by Niklas Schröder on 2008-01-03
good to know.  :)  i'm assuming virtualbox will have similar results (although a little more work will be involved in fixing it.  :p )?

---

