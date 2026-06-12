---
title: "Installing the OS"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by RougeD on 2008-03-28
Hello,
I would like someone's help with this. I know absoulty nothing about installing OS's.
I got this message when I inserted:confused: the CD into my computer. It's a PIII with 2 hard drives one i s 80 GB 
the other is 13GB with 2 RAM chips one for sure I know its 128 and the other not too sure.
The message: BIOS age (1999) fails cutoff (200), acpi=force is required to enable ACPI

---

### Post by T2manner on 2008-03-28
is your computer really old or something?

---

### Post by RougeD on 2008-03-28
well I guess it's pretty old. I just wanted it so I can make all my mistakes on it.

---

### Post by T2manner on 2008-03-28
well.
i'm not an expert but it looks like ur bios is out of date and can't run the ubuntu live cd? 
idk

---

### Post by Zralou on 2008-03-28
It's because its pre Y2K, so the OS won't recognise the BIOS.  Try going to the motherboard website and downloading a BIOS update.

Sara Lou

---

### Post by 3rdalbum on 2008-03-28
I think there's an option to "edit the boot arguments" on the initial menu. Do that, and add the words:

```
acpi=off
```

To the end. Press Enter and the system should boot. If that doesn't work, try what it suggests:

```
acpi=force
```

---

### Post by RougeD on 2008-03-28
Thanks a bunch I will for sure try these tips.

---

