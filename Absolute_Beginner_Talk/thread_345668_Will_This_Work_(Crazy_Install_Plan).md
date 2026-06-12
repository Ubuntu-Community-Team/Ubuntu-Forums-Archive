---
title: "Will This Work?? (Crazy Install Plan)"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by BOBSONATOR on 2007-01-24
Heres How My HD Breaks down right now...

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7431    59689476    7  HPFS/NTFS
/dev/sda2            7432        9465    16338105   83  Linux
/dev/sda3            9466        9726     2096482+  82  Linux swap / Solaris

```

What i am planning to do is break down my sda1 into a 20GIG OSX partition and a 40GIG XP Partion and keep the rest (sda2 &3)

1. My question is, will this all work under grub fine?
2. WIll installing OSX rewrite my grub? 
3. How bout Windows?

---

### Post by Sqwishy on 2007-01-24
> **BOBSONATOR said:**
> 
1. My question is, will this all work under grub fine?
 No i don't think so. you need a separate boot partition for grub

> **BOBSONATOR said:**
> 
2. WIll installing OSX rewrite my grub?  Probobly

> **BOBSONATOR said:**
> 
3. How bout Windows? Yes it will

---

### Post by rabid emu on 2007-01-24
After you do all that mucking about with your HD, just grab any linux install cd and reinstall grub (but nothing else).  it ought to autodetect the new OSes you put on there.

---

### Post by BOBSONATOR on 2007-01-24
> **rabid emu said:**
> After you do all that mucking about with your HD, just grab any linux install cd and reinstall grub (but nothing else).  it ought to autodetect the new OSes you put on there.

Those are my plans.

---

### Post by PriceChild on 2007-01-24
Wait a minute I'll stop you there...

How are you intending on just installing OSX?

---

### Post by BOBSONATOR on 2007-01-24
The x86 Way.

---

### Post by PriceChild on 2007-01-26
What hardware are you planning to put this on?

---

