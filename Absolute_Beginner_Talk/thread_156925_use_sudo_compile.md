---
title: "use sudo compile?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by jipke on 2006-04-08
Is it necessary to use sudo (or a root-terminal) when I want to to compile from source?

sudo ./configure
sudo make
sudo makeinstall

thanks in advance

---

### Post by dermotti on 2006-04-08
Almost always yes.

---

### Post by Sef on 2006-04-08
If you're compiling don't forget to download build-essential first.  Without it, you can't compile.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by sYs^ on 2006-04-08
May I'm wrong, but I think only "make install" needs root privileges.

---

### Post by taurus on 2006-04-08
[QUOTE=sYs^]May I'm wrong, but I think only "make install" needs root privileges.[/QUOTE]
Yes, you only need to user sudo when you run "make install" since you need permission to write to the system.  Otherwise, you can run both ./configure and make as a regular user...
```

./configure
make
sudo make install
-or- 
sudo make checkinstall

```

---

### Post by BoyOfDestiny on 2006-04-08
[QUOTE=taurus]Yes, you only need to user sudo when you run "make install" since you need permission to write to the system.  Otherwise, you can run both ./configure and make as a regular user...
```

./configure
make
sudo make install
-or- 
sudo make checkinstall

```[/QUOTE]

Almost.
sudo make install
or 
sudo checkinstall (if you have installed checkinstall of course :) Frankly I just use checkinstall without sudo, and install the deb with dpkg... )

./configure
make
These do not need root permissions just to reiterate what this poster and the above poster said.

A little screen cap of successful compiles for 64-bit versions. :) [except for zsnes, runs fine in 32-bit chroot though.]
[[IMG]http://img80.imageshack.us/img80/4964/screenshotsrcfilebrowser3hy.th.png[/IMG]](http://img80.imageshack.us/my.php?image=screenshotsrcfilebrowser3hy.png)

Other things useful to get are autogen, automake, autoconf. Just watch for errors when doing ./configure (like something is missing, search for it in synaptic, often libraries have -dev on the end. Those are the ones you want). Happy compiling!

---

