---
title: "Uninstalling a software installed with make and make install"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by Heitor on 2005-09-30
Hello!
How to uninstall a software that was installed with make and make install? Erasing the software's directory is enough?
Thank you.

---

### Post by mlomker on 2005-09-30
Many programs have a **make uninstall** command, but if you already deleted the source directory then deleting the directory may be all that you can do.

---

### Post by Wolki on 2005-09-30
[QUOTE=Heitor]How to uninstall a software that was installed with make and make install? Erasing the software's directory is enough?
[/QUOTE]

As mlomker said. If you don't have the source anymore, it might be completely impossible to remove completely.

To avoid this problem in the future, install the package "checkinstall", and, instead of doing "sudo make install" do "sudo checkinstall". It will create a .deb package and install that, then you can uninstall it easily with Synaptic. Remember to close synaptic before using checkinstall.

---

### Post by Heitor on 2005-10-03
Thank you for the tip on checkinstall :D

---

### Post by mlomker on 2005-10-03
> Thank you for the tip on checkinstall

I've found that it often doesn't work.  If you want to reliably build debian packages then you can take a look at [dh-make and debconf]("http://www.ubuntuforums.org/showthread.php?t=49216").

---

