---
title: "rEFIt on EFI partition vs OS X partition"
date: 2008-10-15
forum: Apple Hardware Users
---

### Post by TheFriesen on 2008-10-15
Hey, relatively new to Ubuntu here.  I got a dual boot on my Mac Mini working properly using rEFIt on my OS X partition.  I'm just curious to know what the benefits are of having the boot loader stored on the EFI partition and if the good outweighs the bad.  I'd imagine a corrupt OS X installation could result in the inability to boot to Ubuntu if rEFIt is stored on the OS X volume?

---

### Post by cyberdork33 on 2008-10-15
> **TheFriesen said:**
> Hey, relatively new to Ubuntu here.  I got a dual boot on my Mac Mini working properly using rEFIt on my OS X partition.  I'm just curious to know what the benefits are of having the boot loader stored on the EFI partition and if the good outweighs the bad.  I'd imagine a corrupt OS X installation could result in the inability to boot to Ubuntu if rEFIt is stored on the OS X volume?

I wouldn't put it on the EFI partition unless you had to. You can install rEFIt to a USB drive and boot from that as a backup.

---

### Post by hajk on 2008-10-17
The good vs the bad?

Good: put that empty (but necessary!) EFI partition to some use.

Bad: need to perform a few more keystrokes when installing rEFIt.

Take your pick...

---

### Post by cyberdork33 on 2008-10-17
> **hajk said:**
> Good: put that empty (but necessary!) EFI partition to some use.
The reason I suggested against using the EFI partition is that if you get a firmware update or something (which is when the partition is actually used by Apple), then we cannot be sure that the rEFIt install will remain untouched.

---

### Post by hajk on 2008-10-17
> **cyberdork33 said:**
> The reason I suggested against using the EFI partition is that if you get a firmware update or something (which is when the partition is actually used by Apple), then we cannot be sure that the rEFIt install will remain untouched.

Good point! Can't be too careful in these matters...

---

