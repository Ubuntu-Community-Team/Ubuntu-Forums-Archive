---
title: "A quistion about GRUB..."
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by kurisutofuaa on 2007-10-05
When installing ubuntu with a grub loader already on the computer will it over-write my previous grub entries or will keep them and just add the grub's boot list?

---

### Post by Pumalite on 2007-10-05
The 2nd.

---

### Post by rsambuca on 2007-10-05
It actually depends on where you install the second grub to.  If you install it to the mbr, then it will overwrite the previous version.  If you install the grub to a new partition, then it will leave the original grub untouched.

---

### Post by kurisutofuaa on 2007-10-05
It's located on the on the mbr.

---

### Post by bodhi.zazen on 2007-10-05
Depends on the version of Ubuntu you install. The gutsy beta releases all over wrote my MBR without asking.

---

### Post by candtalan on 2007-10-05
Although the mbr is overwritten, you would usually expect the existing operating systems (windows and or linux) to be added to the new grub files (menu1st)(?) so that when you boot the newly installed machine, the grub menu displayed is from your new install, but includes all the other existing OS's.
Note if you have a long list on screen, the small down arrow on the right hand side means it will scroll, I often forget to notice this!
good luck

---

