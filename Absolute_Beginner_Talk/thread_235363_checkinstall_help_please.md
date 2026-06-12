---
title: "checkinstall help please"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-08-12
using checkinstall to build and install a package from source.When going thru the prompts it gives me things i can change the onlything i wanted to change was it was currently being built for a i386 architecture. Well i'm running a i686 architecture so i changed it.The app won't build cause it thinks my system is a i386. Here is the complete error message

dpkg: error processing /home/john/Desktop/grsync-0.5/grsync-0.5_0.5-1_i686.deb (--install):
 package architecture (i686) does not match system (i386)
Errors were encountered while processing:
 /home/john/Desktop/grsync-0.5/grsync-0.5_0.5-1_i686.deb

So my question is how do i get my system to show i686 instead of i386?

---

### Post by taurus on 2006-08-13
Maybe because you are using kernel for i386 (default when you install it) while the program is looking for kernel for i686!  Therefore, you might need to install kernel i686 for your machine then...

---

### Post by lime4x4 on 2006-08-13
here is my current kernel

john@ubuntu:~$ uname -r
2.6.15-26-686

The default install was the i386 kernel but i updated to the 686 kernel awhile ago and i also removed all i386 kernels so that the software updater would stop updating them

---

