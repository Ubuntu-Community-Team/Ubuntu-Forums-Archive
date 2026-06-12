---
title: "Is it safe to run fsck on a mounted partition?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by orbital on 2007-05-08
"WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage."

So I was wondering is it safe to run fsck on a mounted filesystem? I think there might be something wrong with my HD.

---

### Post by heimo on 2007-05-08
> **orbital said:**
> "WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage."

So I was wondering is it safe to run fsck on a mounted filesystem? I think there might be something wrong with my HD.

No. Running fsck on a mounted filesystem may cause severe filesystem damage.

Use live cd to boot, and then run fsck on the unmounted filesystem.

---

