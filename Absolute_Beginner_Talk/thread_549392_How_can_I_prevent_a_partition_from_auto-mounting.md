---
title: "How can I prevent a partition from auto-mounting?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by mike984 on 2007-09-12
My HP laptop has a partition called HP_RECOVERY and Ubuntu places an icon for it on my desktop.  

How can I make Ubuntu no longer mount that partition or at least to stop putting an icon for it on my desktop.

Thanks

---

### Post by psusi on 2007-09-12
Edit /etc/fstab and either remote the line for that partition or add the option "noauto" to the options list.

---

### Post by mike984 on 2007-09-12
Thank you!  That did the trick!

---

