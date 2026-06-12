---
title: "Running Windows and Mac in windows"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2006-08-07
i have heard that it is possible to run windows and mac programs in windows in ubuntu...is there a special program i must download to do this or do i just insert the disk? thanks in advance :-k

---

### Post by Klaidas on 2006-08-07
What you're looking for might be VMware, [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by tht00 on 2006-08-07
VMware and qemu are used to run an OS inside of an OS on a virtual machine.  This may work if you've got a fast machine, several extra gigs to devote to an OS virtual machine.


Wine is used to run Windows programs by creating a Windows-like environment (having Windows libraries handy) and the programs actually run inside Linux (rather than a virtual machine).

Crossover Office and Cedega are commercial branches of Wine.  Crossover Office geared more towards normal applications and Cedega towards games.

---

### Post by Sniper99 on 2006-08-07
thanks....where can i get a wine app....that sounds like the best kind of thing to use

---

### Post by tht00 on 2006-08-07
You should be able to find it in Synaptic. (System->Admin->Synaptic)

Make sure the universe and multiverse repositories are turned on.

This should help with that if you haven't done this yet:
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by Sniper99 on 2006-08-07
ok...thanks

---

