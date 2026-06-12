---
title: "more ATI problems, need serious help"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by thespinesplitter on 2005-10-05
i get this when i try to install

```
root@dah-comp:/home/spine # alien -i fglrx-6-8-0_8.16.20-2_i386.deb
dpkg: error processing fglrx-6-8-0_8.16.20-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.16.20-2_i386.deb
root@dah-comp:/home/spine #
```

---

### Post by Ampersand on 2005-10-05
uninstall xlibmesa-gl using 'sudo apt-get remove' or synaptic, making sure that it doesn't try to uninstall the rest of the X server or Gnome, then try again

---

### Post by thespinesplitter on 2005-10-05
THANKS ALOT, and how the hell am i suppossed to go about doing that, i mean making sure ubuntu-desktop doesnt go with it

---

### Post by thespinesplitter on 2005-10-05
and what about xlibmesa-glu? i leave it?

---

### Post by thespinesplitter on 2005-10-05
```
root@dah-comp:/home/spine # alien -d -i /home/spine/Desktop/fglrx_6_8_0-8.16.20-1.i386.rpm
mkdir: cannot create directory `fglrx_6_8_0-8.16.20': File exists
mkdir: cannot create directory `fglrx_6_8_0-8.16.20/debian': File exists
dpkg: error processing fglrx-6-8-0_8.16.20-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.16.20-2_i386.deb

```

---

### Post by thespinesplitter on 2005-10-05
no can do, it wants to take ubuntu-desktop with it

---

