---
title: "ubuntu has spontaneously multiplied"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by namrocks on 2007-05-28
I just rebooted and now in the grub menu I found, for the first time, 2 instances of Ubuntu:

Ubuntu Kernal 2.6.20-16 generic
Ubuntu Kernal 2.6.20-16 generic (recovery mode)
Ubuntu Kernal 2.6.20-15 generic
Ubuntu Kernal 2.6.20-15 generic (recovery mode)

What does this mean? Is it a bad thing? Thanks.

---

### Post by taurus on 2007-05-28
> **namrocks said:**
> I just rebooted and now in the grub menu I found, for the first time, 2 instances of Ubuntu:

Ubuntu Kernal 2.6.20-16 generic
Ubuntu Kernal 2.6.20-16 generic (recovery mode)
Ubuntu Kernal 2.6.20-15 generic
Ubuntu Kernal 2.6.20-15 generic (recovery mode)

What does this mean? Is it a bad thing? Thanks.

You just upgraded to the latest kernel.  That's why you have two entries:  one for new, 2.6.20-16, and one for old, 2.6.20.15 (and two for the recovery mode).  If your new kernel runs fine, you can go into synaptic and remove the old one.  Otherwise, leave the old one there in case there is something wrong with the new version, you can still boot your machine using the old kernel.

---

### Post by namrocks on 2007-05-28
> **taurus said:**
> You just upgraded to the latest kernel.  That's why you have two entries:  one for new, 2.6.20-16, and one for old, 2.6.20.15 (and two for the recovery mode).  If your new kernel runs fine, you can go into synaptic and remove the old one.  Otherwise, leave the old one there in case there is something wrong with the new version, you can still boot your machine using the old kernel.

Thank you.

---

