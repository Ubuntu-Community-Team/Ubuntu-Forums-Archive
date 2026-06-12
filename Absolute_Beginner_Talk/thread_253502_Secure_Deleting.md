---
title: "Secure Deleting"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by JerryC on 2006-09-08
Back in the olden days when I used to use Win XP, I had installed System Mechanic which included a thing called Incinerator.  This would securely delete files by overwriting the space with 0 many times.  I had it set to overwrite 128 times which is supposed to meet military specs.  Is there such a program for linux?

JC

---

### Post by davebgimp on 2006-09-08
> **JerryC said:**
> Back in the olden days when I used to use Win XP, I had installed System Mechanic which included a thing called Incinerator.  This would securely delete files by overwriting the space with 0 many times.  I had it set to overwrite 128 times which is supposed to meet military specs.  Is there such a program for linux?

JC

Well, there's the **shred** command, but I use Wipe.

**sudo aptitude install wipe**

It's command line and I think the default is 36 passes, way more than enough, but you can change it to higher if you're inclined.

---

### Post by JerryC on 2006-09-08
Thank you sir.  Exactly what I was looking for.

JC

---

### Post by yme on 2007-02-20
> **davebgimp said:**
> Well, there's the **shred** command, but I use Wipe.
**sudo aptitude install wipe**

I tried this and got:

yme@yme:/$ sudo aptitude install wipe
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "wipe"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by konst88 on 2007-02-20
It is in the universe. You should enable it.

---

### Post by Bachstelze on 2007-02-20
```
dd if=/dev/zero of=/path/to/file
```

Will overwrite the file with 0's. Repeat the step as many times as you want - you can use a for loop to have it done many times in one command.

---

