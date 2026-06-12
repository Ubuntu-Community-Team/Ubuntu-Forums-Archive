---
title: "dmg2iso error"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by dr-doom on 2007-10-13
Have followed directions on this [thread]("http://ubuntuforums.org/showthread.php?t=135913"), installed perl, used gedit to fix the path for perl, and chmod'd the .pl file, however when i go to execute:

```
dr-doom@Dr-Doom:~/Desktop$ dmg2iso.pl disk2.dmg disk4.iso
dmg2iso v0.2a by vu1tur (vu1tur@gmx.de)

reading property list...found 4 partitions
decompressing:
partition 0
partition 1
partition 2
partition 3
Integer overflow in hexadecimal number at /usr/bin/dmg2iso.pl line 82.
Hexadecimal number > 0xffffffff non-portable at /usr/bin/dmg2iso.pl line 82.
Negative length at /usr/bin/dmg2iso.pl line 85.

```

I have NO idea what that could mean.

Dr. Doom

PowerMac G4 1.07, 1 GB Ram, 121 GB Maxtor IDE HD

---

