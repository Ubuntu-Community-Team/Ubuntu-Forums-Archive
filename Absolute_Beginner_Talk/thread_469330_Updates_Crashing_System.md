---
title: "Updates Crashing System"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by ryan55 on 2007-06-09
I am a new Linux user, only had my system up for about 4 days,  Unfortunately, when I update the system (there are 50 file updates ready for download, including Linux v. 2.6.2.16.28.1), and reboot, the kernel will not start.  I receive "Error 17: cannot load partition."  I am taken to a menu offering the loading of v. 2.6.2.15 and/or 2.6.2.16 and a memtest.  All options produce Error 17 except the "Restore Factory Defaults."  The only thing I have changed on the system prior to installing the updates is the addition of 915resolution.  I am on a Dell 1505n and intel graphics.   Anyone else having trouble?  Anyone have ideas of where to start for some help?  

Thank you.

---

### Post by caro on 2007-06-09
This is a problem unique to the e1505 but it is easily fixed.  I ran into the same problem myself about 1 hour after getting my laptop last week.  Follow these instructions from the Dell forum and you should be set.

[http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update]("http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update")

---

### Post by ryan55 on 2007-06-09
Caro,

Thank you so much.  I ran the test and I did indeed have the output #groot=(hd0.0).  Going to do the fix now.

Again, thank you.

---

### Post by caro on 2007-06-09
Good luck.  Glad I can help.  Being new to Linux, I'm surprised I could help someone else!

---

