---
title: "Boot hangs temporarily"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-03-04
My computer seems to be hanging at the same part on each boot.  Can I reveal the command line to see what specifically is taking so long?

---

### Post by freeflyer57 on 2007-03-04
Where exactly does the boot hang?

---

### Post by bikeboy on 2007-03-04
I'll try to remember the steps, it's not hard.

When the grub boot loader comes up (you may need to press escape), select the option you normally boot from and press the "e" key. Scroll to the end of the line and remove the "quiet", but leave everything else. Then press escape again, and then the "b" key to boot from the modified options.

This change is temporary, but should allow you to see the boot process in more detail. The other option is a program called bootchart, it gives even more detail about how much time everything is taking during the boot up.

---

