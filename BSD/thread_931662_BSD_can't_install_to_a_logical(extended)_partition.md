---
title: "BSD can't install to a logical(extended) partition?"
date: 2008-09-27
forum: BSD
---

### Post by CC_machine on 2008-09-27
it simply doesn't show up in the installer. All i wanted to do was try it out on my laptop, i have ~5 OSes on it (that crappy OS everyone blindly supports, debian, many ubuntus, OpenSuSE)

---

### Post by cardinals_fan on 2008-09-27
That's correct (for now).

---

### Post by Canis familiaris on 2008-09-27
Yes. You can't install BSD in a Logical Drive. You need a Primary Partition. I realized when I installed PC-BSD few weeks ago. I don't think this would be rectified in the future either, because BSDs would soon move to ZFS and ZFS can only be primary partitions. Correct me if I'm wrong.

---

### Post by cardinals_fan on 2008-09-27
> **Anurag_panda said:**
> I don't think this would be rectified in the future either, because BSDs would soon move to ZFS and ZFS can only be primary partitions. Correct me if I'm wrong.
While there are no plans (that I know of) to allow installation to logical partitions, it's wrong to say that "BSDs will soon move to ZFS", because that varies per BSD.  FreeBSD is moving fairly aggressively towards ZFS, but NetBSD is only aiming for experimental support, with no plans to use it as a primary installation file system at this time.

---

