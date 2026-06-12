---
title: "is it safe to remove the -386 kernel images?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-18
been running the 686 kernel images. I was wondering if it's safe to remove the 386 kernel images using synaptic and if so how do i edit the grub menu so there not listed anymore?

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **lime4x4 said:**
> been running the 686 kernel images. I was wondering if it's safe to remove the 386 kernel images using synaptic and if so how do i edit the grub menu so there not listed anymore?

Yes, it is safe to remove old kernels. When they are uninstalled, their entries are removed from the grub menu.lst.

---

### Post by jeremy on 2006-07-18
I use 686, but keep the 386 to fall back on if there is a problem with an update.

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **jeremy said:**
> I use 686, but keep the 386 to fall back on if there is a problem with an update.
That's not completly nessesary, he might have old 686 backups and he should be ok when removing it since if a kernel is installed and it works, it will generally stay working.

---

### Post by lime4x4 on 2006-07-18
well i have 3 other 686 kernels plus the 386 kernel so i do have backups..Just tired of synaptic always wanting to update the 386 kernel..

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **lime4x4 said:**
> well i have 3 other 686 kernels plus the 386 kernel so i do have backups..Just tired of synaptic always wanting to update the 386 kernel..

It is safe to remove the 386 kernels. Plus, you have plenty of backups incase something goes wrong.

---

### Post by toasted on 2006-09-15
So, it would be these then:

linux-restricted-modules-386
linux-restricted-modules-2.6.15-26-386
linux-restricted-modules-2.6.15-23-386
linux-image-386
linux-image-2.6.15-26-386
linux-image-2.6.15-23-386
linux-headers-2.6.15-26-386
linux-386

Basically anything that has a -386 after it, correct?

---

### Post by toasted on 2006-09-15
Nevermind
I found out that you just mark the image in Synaptic and the rest is taken of for you. It even removed the grub entries!!

---

