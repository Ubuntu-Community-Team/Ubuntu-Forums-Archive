---
title: "Two Kernels at Boot Screen - Normal?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-06-21
Hi,
Since I allowed some updates I seem to be blessed with the option of booting in 2.6.20-16 generic and 2.6.20-15 generic. The default is 2.6.20-16.
Is this a good or bad thing?
I know no difference or if one should be there and the other not, or how to rid the one that shouldn't be there.
Ubuntu user since Monday.
Warm Regards
Bill

---

### Post by skymera on 2007-06-21
i had that.
i forgot what file i editied, somethnig like boot.ini

i deleted the entry on ***-15 and kept ***-16

works :)
hopefully someone knows the exact file

---

### Post by Nekiruhs on 2007-06-21
Yep, that means you got a kernel update. GRUB does this by default so that if you break the 16 kernel you can "fall back" on the 15. If the 16 kernel works for you use it. If not, just comment out those lines (put a # sign before each line) that have the 16 kernel in your menu.lst (gksudo gedit /boot/grub/menu.lst).

---

### Post by overdrank on 2007-06-21
> **wapfu said:**
> Hi,
Since I allowed some updates I seem to be blessed with the option of booting in 2.6.20-16 generic and 2.6.20-15 generic. The default is 2.6.20-16.
Is this a good or bad thing?
I know no difference or if one should be there and the other not, or how to rid the one that shouldn't be there.
Ubuntu user since Monday.
Warm Regards
Bill

Hi and welcome   I would advise to leave it there if you were to do more updates then if something happen to your system you might be able to use that to boot into ubuntu and maybe even save your data,:popcorn:

---

### Post by Nekiruhs on 2007-06-21
> **skymera said:**
> i had that.
i forgot what file i editied, somethnig like boot.ini

i deleted the entry on ***-15 and kept ***-16

works :)
hopefully someone knows the exact file
I would recommend restoring the lines for the 15. It can be very useful if you break something later. This function is not a problem or an error. the file is /boot/grub/menu.lst. To edit it type
```
gksudo gedit /boot/grub/menu.lst
```
Next time you change something, it is also advisiable not to delete the lines, rather to comment them out (with a # at the beginning of the line). it acheives the same result as deleting but you can restore it much easier.

---

### Post by jputman01 on 2007-06-21
i would just leave it for now, i wait until i have 3 then i comment out the oldest and leave the two newest so i can always fall back, which has helped me greatly in recent times

but to answer your question...yes that is totally normal

---

### Post by skymera on 2007-06-21
> **Nekiruhs said:**
> I would recommend restoring the lines for the 15. It can be very useful if you break something later. This function is not a problem or an error. the file is /boot/grub/menu.lst. To edit it type
```
gksudo gedit /boot/grub/menu.lst
```
Next time you change something, it is also advisiable not to delete the lines, rather to comment them out (with a # at the beginning of the line). it acheives the same result as deleting but you can restore it much easier.

oops, so how do i get the 15 back?
i forogt to just # it out

---

### Post by Nekiruhs on 2007-06-21
It would depend on your harddrive partitioning. I would make a new thread to see if you could get that sorted out by someone who knows a bit more 'bout GRUB.

---

### Post by wapfu on 2007-06-21
Thanks to all,
Appreciate the assistance.
Best Regards
Bill

---

