---
title: "MTRR Help!"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Zennlavian on 2007-07-23
can anyone tell me if this looks OK.  I'm running a Pentium IV, 2.8 ghz, 2gb ram, nVidia TNT2 model 64

zennlavian@Linux-Desktop:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1

I've noticed my file browser & Firefox running slower than I'd like.

---

### Post by ddrichardson on 2007-07-23
> **Zennlavian said:**
> can anyone tell me if this looks OK.  I'm running a Pentium IV, 2.8 ghz, 2gb ram, nVidia TNT2 model 64

zennlavian@Linux-Desktop:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1

I've noticed my file browser & Firefox running slower than I'd like.

Yep, a single 2048Mb memory chip.

---

### Post by Zennlavian on 2007-07-23
no.  I actually have 2 1gb chips.  I checked the bios and it states that it's running in dual channel mode.

---

### Post by ddrichardson on 2007-07-23
> **Zennlavian said:**
> no.  I actually have 2 1gb chips.  I checked the bios and it states that it's running in dual channel mode.

Its the same difference in dual channel mode - they're running as a matched pair, memory type range registers only tell the system what the memory range is and how to access.

---

### Post by Zennlavian on 2007-07-23
thanks for the reply.

---

