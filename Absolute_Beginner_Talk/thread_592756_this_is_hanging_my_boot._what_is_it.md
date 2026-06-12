---
title: "this is hanging my boot. what is it?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-26
ok i found out whats hanging my boot.
from dmesg i get this:

```

[   32.798159] Adding 2698912k swap on /dev/sda3.  Priority:-1 extents:1 across:2698912k
[   33.159667] EXT3 FS on sda2, internal journal
[   34.726828] Failure registering capabilities with primary security module.
[   72.408464] NET: Registered protocol family 17
[   73.263954] wlan0: Initial auth_alg=0

```

why is it adding stuff on swap??
more importantly why is therw a jump from 34 to 72?

---

### Post by ddrichardson on 2007-10-26
That's just swap space being initialised. Are you using ndiswrapper?

---

### Post by skymera on 2007-10-26
nope.
my pci works out of the box


but stil, whats that big jump?

---

### Post by oilchangeguy on 2007-10-26
> **skymera said:**
> ok i found out whats hanging my boot.
from dmesg i get this:

```

[   32.798159] Adding 2698912k swap on /dev/sda3.  Priority:-1 extents:1 across:2698912k
[   33.159667] EXT3 FS on sda2, internal journal
[   34.726828] Failure registering capabilities with primary security module.
[   72.408464] NET: Registered protocol family 17
[   73.263954] wlan0: Initial auth_alg=0

```

why is it adding stuff on swap??
more importantly why is therw a jump from 34 to 72?

the big jump is because these are the only items where there is possibly some issue during startup. and why do you have so much swap? from your signature it looks like your computer has 1 gb of ram. if so, you could get by with 256mb of swap. there is no reason to have this much swap space. you're just wasting hard drive space. you do understand that virtual ram (swap) is much slower than physical ram. and if your computer needs to use virtual ram, it's got problems.

---

### Post by skymera on 2007-10-27
yes i know, that was a spare 2.6GB at the end of my 500gig drive.

so meh, my not?

---

### Post by oilchangeguy on 2007-10-27
> **skymera said:**
> yes i know, that was a spare 2.6GB at the end of my 500gig drive.

so meh, my not?

you mind translating that second line, into english?

---

### Post by skymera on 2007-10-27
sorry :P

so meh, why not?

---

### Post by ddrichardson on 2007-10-27
Have you tried using bootchart to see what is taking the time up? It's in main.

---

