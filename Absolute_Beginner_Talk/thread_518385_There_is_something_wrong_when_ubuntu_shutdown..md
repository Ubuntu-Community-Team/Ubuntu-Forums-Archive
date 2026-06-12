---
title: "There is something wrong when ubuntu shutdown."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by zacharyt on 2007-08-05
Instead of halting, it restarts...how to deal with that? Thanks^^

---

### Post by skymera on 2007-08-05
try

sudo shutdown -P now

not the CAPS P

replace now with number for minutes

---

### Post by zacharyt on 2007-08-05
sudo shutdown -P now
i still restarted,

maybe it is something about BIOS?

---

### Post by por100pre1 on 2007-08-05
Are you using an ethernet card? I heard that some of them can turn on a PC, can that happen with Ubuntu? :confused:

---

### Post by zacharyt on 2007-08-05
i am using an ethernet card..

---

### Post by Raineer on 2007-08-05
> **zacharyt said:**
> i am using an ethernet card..
There is a BIOS setting called "Wake on LAN", which is what the person above is implying.  Make sure this is turned off.

---

### Post by por100pre1 on 2007-08-05
Weird. Normally this should work:

```
sudo shutdown -h now
```

---

