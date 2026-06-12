---
title: "Doing my first compile"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-05-24
Hi,

I'm doing my first compile (for linux) of a tool for mySQL 5.  I'm getting the following error:

```

checking for glib-2.0 libxml-2.0 >= 2.6.2... Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found
configure: error: Library requirements (glib-2.0 libxml-2.0 >= 2.6.2) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

Now obviously it's looking for glib-2.0 and not finding it.  However, the only thing I can find in the repository that matches this seems to be installed:
```

The GLib library of C routines
GLib is a library containing many useful C routines for things such
as trees, hashes, lists, and strings.  It is a useful general-purpose
C library used by projects such as GTK+, GIMP, and GNOME.

This package contains the shared libraries.

```

The exact name and version from the repository is:
Package: libglib2.0-0

Installed Version: 2.8.3-0ubuntu1
Latest Version: 2.8.3-0ubuntu1

Am I missing something in my complete n00b-ness?

---

### Post by mostwanted on 2006-05-24
Is there a glib-2.0-dev package? Usually you need the *-dev packages when you're compiling.

---

### Post by the gnome on 2006-05-24
You are indeed correct sir, many thanks!

---

