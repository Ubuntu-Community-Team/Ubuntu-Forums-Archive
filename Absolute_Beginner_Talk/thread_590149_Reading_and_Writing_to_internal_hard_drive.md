---
title: "Reading and Writing to internal hard drive"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Ruhoo246 on 2007-10-24
I looked around a bit and couldn't quite find what i was looking for.  I have Ubuntu on a 4 gig jump drive, so space is limited.  I can read from my internal hard drive, and was wondering if i can write to it, and if so how i would go about doing so.
Thanks for your time!

---

### Post by Inxsible on 2007-10-24
What file system does your internal drive have?

If its NTFS, and you are using Feisty Fawn, you will have to install ntfs-3g to be able to write to that drive.

---

### Post by Hospadar on 2007-10-24
> **Inxsible said:**
> What file system does your internal drive have?

If its NTFS, and you are using Feisty Fawn, you will have to install ntfs-3g to be able to write to that drive.

Also install ntfs-config, which can be run from a terminal "ntfs-config" and will help set up your drives for read/write support.

---

### Post by Ruhoo246 on 2007-10-26
the internal hard drive is windows XP media center edition

---

