---
title: "External harddrive not seen"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2007-02-15
I installed a harddrive in an external enclosure formatted FAT32 and attached to the computer via firewire. Windows sees the drive-no probelm. But after booting to Ubuntu the drive is not seen. How can I make Ubuntu see the attached drive? Thanks.

---

### Post by skyhopper88 on 2007-02-15
Try entering
> sudo mount -a

---

### Post by ajmorris on 2007-02-15
> **jmtjet said:**
> I installed a harddrive in an external enclosure formatted FAT32 and attached to the computer via firewire. Windows sees the drive-no probelm. But after booting to Ubuntu the drive is not seen. How can I make Ubuntu see the attached drive? Thanks.

also you must edit your "/etc/fstab" if you wish it to mount automatically.

---

### Post by jmtjet on 2007-02-15
Ok, got it mounted. Now how do I edit  "/etc/fstab" file. Thanks a million. :)

---

### Post by jmtjet on 2007-02-16
Update: Got it all sorted. Thanks. :)

---

