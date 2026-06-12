---
title: "Gutsy freezing on Live CD"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-12-03
When installing Gutsy on this system (currently running Feisty) install freezes at the import previous users and settings wizard, just after choosing which drive to format.

Feisty installs fine, Gutsy will not. 

I know there are alternate CDs, and text based installers, but downloading and burning 700Mb+ just isn't attractive right now. 

(tried 4 different Ubuntu shipit Gutsy Live CDs, same problem each time)

- Matt

---

### Post by philinux on 2007-12-03
What are your system specs?

---

### Post by Old Pink on 2007-12-03
Erm, 2.66Ghz Pentium 4, 768Mb RAM, 80GB Hard Drive.

Fresh installs Dapper and Feisty well. Just gutsy, so not a system problem...

---

### Post by jaybombalous on 2007-12-03
where are u trying to import the user settings from? Why are u trying to do this?


The install is not freezing, the importing of user settings is. thats your problem, try installing without importing.

---

### Post by philinux on 2007-12-03
you forgot graphics card make and model

---

### Post by Old Pink on 2007-12-03
> **jaybombalous said:**
> where are u trying to import the user settings from? Why are u trying to do this?


The install is not freezing, the importing of user settings is. thats your problem, try installing without importing.
That's my aim. Once I select partition it searches to see where it can import from, and that's where it freezes.

If I could make it skip the step, I would. I don't want it to import. At all. 

As for graphics card, it's shared memory with the RAM, and lspci says:
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by philinux on 2007-12-03
ah sorry misread post. Best thing is to move home to separate partition then when installing mark it as dont format. That way all you app settings will be preserved.

---

### Post by Old Pink on 2007-12-03
No, again, that's wrong. 

No matter what I mark as format or not format, directly after choosing, it searches ALL partitions for users and settings. At this point it freezes.

To conclude:
[LIST]
[*]CD freezes during Install process on Live CD
[*]DON'T want to import settings
[*]CAN'T skip step[/LIST]Basically:

At a certain point in install process, it scans all drives/partitions for existing information. At this point, the system freezes beyond usage.

---

### Post by Old Pink on 2007-12-03
Marking *all *drives for format makes it skip the import stage, and I can proceed right to the confirmation before installation starts without fail.

Going back and marking partitions as not format then brings up the same trouble again. Literally no mouse movement, keyboard non-responsive, even ALT + SysRq + REISUB does nothing.

---

### Post by Old Pink on 2007-12-04
Right, went through with the mass format.

Gets to "formatting swap space in partition #2" and it freezes up

---

### Post by jaybombalous on 2007-12-04
I have never had import **** when I was installing from the alternate CD image.

---

