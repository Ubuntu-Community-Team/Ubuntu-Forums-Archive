---
title: "Xubuntu still won't shutdown"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by apunc1 on 2007-01-13
I am using an Xubuntu 6.06 and It hangs at the splash screen at shutdown as described here

[http://www.ubuntuforums.org/showthread.php?t=288735&page=2&highlight=xubuntu](http://www.ubuntuforums.org/showthread.php?t=288735&page=2&highlight=xubuntu)

when i try to do the prescribed solutiion by editing the end of the menu.lst with acpi=force, i get the error "Can't open file to write" when i try to save. 
I also noticed that I can't su in a terminal. When I try to and enter my password, it says "Authentication failure". I thought maybe the username wasn't give su privileges (eventhough it's the only one i set up), so I booted in recovery mode and entered
 addgroup username admin
 entering my username. It said my username is already a part of admin.

What could be the problem?

This was a clean install on an older compaq  (i'm not sure of the processor speed, but it was bought in 99) with 192 mb of ram.

Edit: I'm not sure if this is the correct usage of su.

---

### Post by apunc1 on 2007-01-13
> **apunc1 said:**
> I am using an Xubuntu 6.06 and It hangs at the splash screen at shutdown as described here

[http://www.ubuntuforums.org/showthread.php?t=288735&page=2&highlight=xubuntu](http://www.ubuntuforums.org/showthread.php?t=288735&page=2&highlight=xubuntu)

when i try to do the prescribed solutiion by editing the end of the menu.lst with acpi=force, i get the error "Can't open file to write" when i try to save. 
I also noticed that I can't su in a terminal. When I try to and enter my password, it says "Authentication failure". I thought maybe the username wasn't give su privileges (eventhough it's the only one i set up), so I booted in recovery mode and entered
 addgroup username admin
 entering my username. It said my username is already a part of admin.

What could be the problem?

This was a clean install on an older compaq  (i'm not sure of the processor speed, but it was bought in 99) with 192 mb of ram.

Edit: I'm not sure if this is the correct usage of su.

Edit again: sorry. i can sudo. I reverted back to su from my suse days somehow 
:-k

---

