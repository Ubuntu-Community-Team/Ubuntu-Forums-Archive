---
title: "Just Wondering"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by johnbull on 2007-09-05
Why ubuntu insists all my mass storage devices are SCSI?

They aren't, they're IDE (1 Maxtor HD, 1 Hitachi HD, 1 Samsung CD/DVD RW and 1 Sony CD/DVD ROM) but Device manager insists they are SCSI.

Not that bothered, however, everything working just fine.

---

### Post by asmoore82 on 2007-09-05
I believe that the code that started out to just support SATA devices has become so reliable,
flexible and powerful that it will eventually completely replace the old IDE code.
for now, some platforms remain unaffected while others are already using
**libata** for IDE devices causing them to show as SCSI(the future).

---

### Post by nowshining on 2007-09-05
feisty was the first to use scsi drivers exclusively...

---

