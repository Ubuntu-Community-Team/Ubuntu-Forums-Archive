---
title: "repartitioning but not reinstalling"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-09-13
If I want to resize my partitions, can I use the Live CD until the point of installation and then just cancel? Does this preserve my partition changes?

Thanks,
John

---

### Post by jordanmthomas on 2006-09-13
You can use the LiveCD and then go to System --> Administration --> Gnome Partition Editor
If you make changes and apply them here, it will be done for good.

---

### Post by JohnJSal on 2006-09-13
Ah, so I just go into the Live version of Ubuntu instead of the installation process?

---

### Post by jordanmthomas on 2006-09-13
I'm not entirely sure what you mean.

You boot off the CD.
The desktop comes up with an install icon...but you don't click it.  Instead, you run the partition editor manually.

I think you've got the right idea, but if I am not making sense, could you clarify what you think you need to do?

---

### Post by confused57 on 2006-09-13
You might want to try the gparted live cd(30 mb download):

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Here's some screenshots:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by wieman01 on 2006-09-13
I've just gone throug the process. Yes, just boot the LiveCD and fire up the Partition Editor as mentioned in here. You can remove partitions, copy & move them, change the size, etc.

But be careful... If you move partitions like /home, /, or /SWAP, you may have to adjust GRUB and "/etc/fstab" which is tricky. Let us know if you need help. No rocket-science.

---

