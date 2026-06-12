---
title: "Disk Maintenance"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-04-22
Afternoon all, or good morning America

I noticed that whilst booting up today Edgy went into some kind of disk check. Everything appears to be cool but should I be running some kind of regular check disk type utility.

Many Thanks.

---

### Post by heimo on 2007-04-22
> **linuxforrealpeople said:**
> I noticed that whilst booting up today Edgy went into some kind of disk check. Everything appears to be cool but should I be running some kind of regular check disk type utility.

No, because checks are run regularly for you. :) Every N(* mounts your filesystem is forced to be checked. It can be changed using tune2fs. 


*) I think default is something like 30.

EDIT: Just created an ext3 filesystem and it says:
> This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first.

---

### Post by linuxforrealpeople on 2007-04-22
Many Thanks.

---

