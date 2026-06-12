---
title: "disk format utility"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-16
is there a formatting utility in Ubuntu 7.10 that allows you to view ALL installed disks (even ones that are not yet formatted) and format them as needed?  looking for the equivalent of Disk Management console in Windows.  thanks.

---

### Post by Rocket2DMn on 2008-01-16
Gparted is what is used on the live cd, but you can download it from the repositories to use directly from Ubuntu (you just can't modify your root partition since a partition has to be unmounted to modify).

---

### Post by p_quarles on 2008-01-16
Gparted. You can use it view all disks -- but you can't use it to modify a currently mounted drive. For that, you need the Gparted Live CD.

---

### Post by jimartin8219 on 2008-01-16
Try using **PYSDM**  I think this might help.  I know it helped me.  Install the program using the package manager then reboot and run the program.

Hope this helps,

---

