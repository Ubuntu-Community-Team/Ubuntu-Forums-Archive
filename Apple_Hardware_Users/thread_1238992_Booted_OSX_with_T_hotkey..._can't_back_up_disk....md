---
title: "Booted OSX with T hotkey... can't back up disk..."
date: 2009-08-13
forum: Apple Hardware Users
---

### Post by aqua_scummm on 2009-08-13
I have an iMac G4 running OSX 10.3 (IIRC).  It's got a double partitioned hard drive, and I booted the system with the T hotkey, essentially making it a Firewire external HD.

I don't have the ownership permissions of the drive, so I tried changing them with chown -R, but that fails, saying "Read-only filesystem"...


Is there any way around this you can think of?  The Mac writes to its own drive just fine...


Thanks!

---

### Post by aqua_scummm on 2009-08-13
I might be okay... I think sudo cp -R is working on copying, then I should be able to chown -R the whole disk... we'll see if anything flashes before my eyes as the terminal windows do they're job, silently working, though you would never know the vast amounts of data being copied...

---

