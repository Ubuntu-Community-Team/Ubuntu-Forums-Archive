---
title: "seamonkey1.1 can't load 'libsmooth.so'!?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by matiz on 2007-01-23
:confused: 

After successfully install the seamonkey 1.1.
I'm use the 'seamonkey-1.1.en-US.linux-i686-gtk1.installer', for the 'seamonkey-1.1.en-US.linux-i686.installer' gave me a 'Segmentation fault' even can not install.

After test runing seamonkey in english xwindow, I turned to my local korean environment, when start the seamonkey, it gave me an ugly small fonts, and run seamonkey from the terminal, it says:

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so"

after running command locate libsmooth.so, the system tells me: 
/usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so

I have done a soft link
ln -s /usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so
to the installation directory, and restarted the seamonkey, comes the same problem.

how to fix this?

---

