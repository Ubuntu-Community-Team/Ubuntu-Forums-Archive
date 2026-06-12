---
title: "Boot Ubuntu from a directory on HFS+?"
date: 2007-05-14
forum: Apple PPC Users
---

### Post by WaferMouse on 2007-05-14
Is it at all possible to boot Ubuntu off a directory on a HFS+ partition? Y'know, so you can keep both OSs on the same drive, not have to partition them away. Specifically I've got an indigo iBook with a CD drive that I've ordered a new HDD for that I've had a lot of Ubuntu fun in the past with.

---

### Post by Gen2ly on 2007-05-14
I don't think the installer could be make to do that.  It is pretty specific where it will allow an install.  It is possible if you use a distro like Gentoo that this might be possible.  By specifying it in the file fstab.  Tell you the honest truth this wouldn't be the best idea anyhow as if HFSplus is ever a misread or error the partition will be marked read-only - and that can have bad bad effects.  Partitioning isn't that difficult and is pretty safe nowdays.

---

### Post by stmiller on 2007-05-14
> **WaferMouse said:**
> Is it at all possible to boot Ubuntu off a directory on a HFS+ partition? Y'know, so you can keep both OSs on the same drive, not have to partition them away. Specifically I've got an indigo iBook with a CD drive that I've ordered a new HDD for that I've had a lot of Ubuntu fun in the past with.

Nope. :)

I do have a friend who uses an external USB hard drive with his iBook G4 to boot Debian PPC off of that external drive. So that is possible, but tricky to set up.

---

