---
title: "Sharing /home"
date: 2008-06-15
forum: Arch and derivatives
---

### Post by intense.ego on 2008-06-15
I am considering trying out Arch Linux because of the good things I have heard about it from other forum members. It is pretty hard to install for a non-expert like me (from what I've heard and read at least), but I am willing to give it a try. My question is, is it possible and safe (for the data) to share a /home parition between ubuntu and arch or will they not behave well together? If this is possible, it would mean i could essentially have two distros for the space of one (my root for ubuntu is only 3 gb anyway).

---

### Post by Barrucadu on 2008-06-15
Well, assuming your user on Arch has the same UID as your user on Ubuntu, you will be fine. You can make sure this is the case by specifying the UID when adding your user.

---

### Post by mips on 2008-06-16
Personally I would not share /home between distros. There could be possible conflicts.

If you follow this to the letter you will be fine, [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

Another resource is [http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by handy on 2008-06-16
+1

I would not share /home you are sure to cause confusion to one distro' or the other.

You could share another data partition without any problems at all though.

---

### Post by Pogeymanz on 2008-06-19
I always share /home. I just make sure that I use a different user name and there will be no conflicts.

---

### Post by handy on 2008-06-22
I find it most convenient to use the same user name & password on all my systems & for root as well.

Courses for horses eh!

---

