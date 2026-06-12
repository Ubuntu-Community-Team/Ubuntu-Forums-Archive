---
title: "Need to edit my GRUB boot list...."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2008-02-19
I need to add : BackTrack 3 on hda3. I am trying to configure a triple boot laptop. hda1 is XP and hda2 in Ubuntu. I have everything on, just need to add grub entries.

---

### Post by bodhi.zazen on 2008-02-19
```
gksu gedit /boot/grub/menu.lst
```

Add 'em in ...

---

### Post by dwblas on 2008-02-19
If you are asking how I don't think you should edit the file yourself.  Try something like this as it should leave you with a Grub that you can boot from.  Have a rescue CD handy before you do anything with grub and back-up the original file.  There is always that one stupid mistake that prevents a boot.
[http://freshmeat.net/projects/grubconf/](http://freshmeat.net/projects/grubconf/)

---

