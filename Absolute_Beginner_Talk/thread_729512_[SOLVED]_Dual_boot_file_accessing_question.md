---
title: "[SOLVED] Dual boot file accessing question"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Nerdriot on 2008-03-19
Hi, just a quick question...

On this machine (not mine), Windows XP is installed first, and I installed Gutsy on a partition.

Now, I've noticed that I can access files from the Windows partition, so I was wondering if you can do the same thing from the Windows side.

Anyone know?

Thanks in advance!

---

### Post by mikewhatever on 2008-03-19
Yes, you'll need a driver to make Windows recognise ext3 file system.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Nerdriot on 2008-03-19
Oh ok, thank you! I was going to ask a very stupid question, then logic stopped me. "So it's not possible without this?" Obviously not, or it wouldn't require the driver... ;)

Thanks again!

---

### Post by glennric on 2008-03-19
I recommend ext2fsd.
[http://ext2fsd.sourceforge.net/index.htm]("http://ext2fsd.sourceforge.net/index.htm")

---

### Post by mikewhatever on 2008-03-20
> **Nerdriot said:**
> Oh ok, thank you! I was going to ask a very stupid question, then logic stopped me. "So it's not possible without this?" Obviously not, or it wouldn't require the driver... ;)

Thanks again!

It's ok to ask questions. None of use had known what we do when we started.

---

