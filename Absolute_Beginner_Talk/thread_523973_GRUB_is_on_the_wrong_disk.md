---
title: "GRUB is on the wrong disk"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by ashkev on 2007-08-12
I have a computer with two hard drives.  I installed Windows XP on one and Edubuntu on the other.  My problem is that when I try to boot, I get an error stating unable to locate OS.  I can but with Gboot, and if I say boot from MBR from second disk GRUB loads, and I can choose my OS from there.  What have I done wrong, and how can I fix things so I don't need to boot from Gboot.

Thanks

---

### Post by uclalinux on 2007-08-12
see if you can change the which hard drive to boot from in the bios, that way you look at the MBR on your 2nd hard drive 1st.

---

### Post by ashkev on 2007-08-12
That worked like a charm.  

Thanks

---

