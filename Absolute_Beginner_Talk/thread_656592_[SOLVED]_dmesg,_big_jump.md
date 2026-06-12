---
title: "[SOLVED] dmesg, big jump"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-01-02
ok well not so big
but from 0 to 17

```

[    0.000000] Detected 1862.091 MHz processor.
[   17.190035] Console: colour VGA+ 80x25

```

why does detecting processor take so long?

---

### Post by skymera on 2008-01-02
bump

---

### Post by skymera on 2008-01-03
anyone?

is it normal, if it is then i be quiet :)

---

### Post by rubicon on 2008-01-03
My:
```

[    0.000000] Detected 2992.720 MHz processor.
[   24.105330] Console: colour VGA+ 80x25
```

I guess it just initializes timers, so before processor detection timestamps is always [    0.000000], though actually there must have been [1.000000] and so on.

Is this bothering you now? :)

---

### Post by skymera on 2008-01-03
no :P

i wasd just curious :)

---

