---
title: "Compiling error"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Glass_Onion on 2006-06-25
I'm trying to compile Gaim 2 beta3 and am getting this error. 

```
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.10.0, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at http://www.gtk.org/.

```

I've tried running ldconfig which didn't give me any feedback, editing /etc/ld.so.conf but that's a blank file so not much I could learn from that. And after that I'm pretty much out of ideas. I was getting an error a long the lines of Glib either not being there or not greater than or equal to v2 so I installed the latest stable version I could find on gtk.org. ANybody have any ideas on what to do next?

---

### Post by illynova on 2006-06-25
I'm not currently running on ubuntu, so I don't remember the package name - but look around in apt for something called "glib2-dev"

---

### Post by tonyr on 2006-06-25
I'm running an updated version of Dapper, and when I run
```

pkg-config --modversion glib-2.0

```

it returns 2.10.3.  I would suggets reinstalling **libglib2.0-0**.  Make sure **libglib2.0-dev**
and **libglib2.0-data** are also installed and that they are all the same version.  
Synaptic should show you what versions of **libglib** packages are installed.  I would
reinstall any packages in a terminal with **apt-get** like this:
```

sudo apt-get install -reinstall glib2.0-0

```

---

