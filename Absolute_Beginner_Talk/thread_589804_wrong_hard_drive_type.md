---
title: "wrong hard drive type"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Capt on 2007-10-24
I just  installed v7.10. One problem I am having is that my hard drives are listed as SCSI instead of IDE. In fdisk they show as sdb...... Any way I can correct this?

---

### Post by julian67 on 2007-10-24
This is normal, it's been the default behaviour in Linux for a while. All HDDs, both IDE and SATA,  now use the same interface to the kernel so they will all be /dev/sd*.  I think there are a few exceptions but this is the general rule.

---

### Post by Capt on 2007-10-24
Thank you much....I wasn't aware of that.

---

