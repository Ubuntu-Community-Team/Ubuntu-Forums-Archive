---
title: "Are any of my partitions suitable for access?"
date: 2009-01-04
forum: Apple Hardware Users
---

### Post by dandelions on 2009-01-04
I've finally got round to getting my Intrepid install in a usable state (wireless internet access, themes, etc) and the last thing I have left to do is share my Firefox and Thunderbird profiles between it and my usual operating system, Leopard. This is where I run into problems.

Currently, this is how my disk is partitioned:
200mb EFI partition
100gb HFS+ partition (for OS X v10.5, journaled, 70gb free)
1gb Ubuntu swap partition
10gb ext3 partition (for Intrepid Ibex, 4.5gb free)

Are any of these partitions writeable by both Ubuntu and OS X? I can read the HFS partition in Ubuntu, and the ext3 partition in OS X, but for this to work, I'm fairly certain I need somewhere that's got full *write* access.

I don't have a Windows partition of any type (ntfs, fat32, etc) because I run Windows XP and 95 through virtual machines in OS X - ie, they're stored as part of the journaled HFS+ partition.

Any suggestions, or am I going to have to create a new partition altogether? If so, which type, and what would be the safest way to go about resizing my existing partitions?

---

### Post by cyberdork33 on 2009-01-05
you can read/write hfs+ in Ubuntu if disable journaling, though it isn't really recommended.

---

### Post by dandelions on 2009-01-05
Yeah, I'm not keen on that because I'm likely to use OS X as my primary OS, and I don't want to damage it.

---

### Post by cyberdork33 on 2009-01-05
> **dandelions said:**
> Yeah, I'm not keen on that because I'm likely to use OS X as my primary OS, and I don't want to damage it.
then the answer is no.

---

