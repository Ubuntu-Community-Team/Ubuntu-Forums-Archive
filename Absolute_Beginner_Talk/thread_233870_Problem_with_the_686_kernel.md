---
title: "Problem with the 686 kernel"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by sapphire56 on 2006-08-10
I downloaded the 686 kernel because i read it could make my system faster

but when i try to bott with the 686 kernel i get ar kernel panic and sometging about an syncing error

i can use the a 368 kernel so its not a big deal but i would really like to get my system a little faster

---

### Post by kinematic on 2006-08-10
what processor do you have?
if you've installed the wrong kernel for your processor the kernel simply won't boot.

---

### Post by sapphire56 on 2006-08-10
i have a Intel P4 Prescott with hyperthreading

---

### Post by kinematic on 2006-08-10
i must admit that i'm not all to familiar with intel but i think that one belongs to the i586 architecture.
ubuntu doesn't have an i586 specific kernel as far as i know so i think you'll have to stick with the 386 kernel.
but maybe someone else can comment on this.....

---

### Post by Metacarpal on 2006-08-10
The i586 family refers specifically to the first series of Pentium processors.  i686 is P3 and up, though some would argue that all but the earliest P4s should be a new classification entirely.

The linux-686 metapackage should work quite well with your system.  Perhaps you just got a faulty download, or it didn't install quite right.

Reboot, and when GRUB first starts hit Esc.  Then choose your previous kernel to boot.  Uninstall and reinstall linux-686.  Hopefully, that'll fix you up.

---

### Post by sapphire56 on 2006-08-10
thanks i'll try that

---

