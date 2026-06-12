---
title: "uninstalling non-packaged programs"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by helix26 on 2007-06-13
Trying to uninstall glib-2.10, though I don't see it on the Synaptics package manager as a package I can remove. I've successfully configured, made and installed glib-2.12.11, and would like to use the new version...

Any idea how I can remove it, or change my environmental variables so that, when I do compile, I use the glib-2.12 libraries instead of the 2.10?

Full text of the warning:

```

*** 'pkg-config --modversion glib-2.0' returned 2.12.0, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files no configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.

```

If fixing the LD_LIBRARY_PATH is all that would be required, let me know how to do that, please. I searched for it in the configure script, but they all ended up being pointers to the variable, not altering the variable itself.

Thanks in advance.

---

### Post by Bachstelze on 2007-06-13
Instead of letting it autodetect it, you should be able to pass a parameter to the configure script to tell it the path to glib. That way, you can tell it to use the new one, it's a bad idea to uninstall the old one.

---

### Post by HotShotDJ on 2007-06-13
Don't screw with your system libraries.  You will wreck your system.  If this is the kind of thing you would like to do, perhaps a distribution like [Gentoo]("http://www.gentoo.org") or [Linux from Scratch]("http://www.linuxfromscratch.org") would be more to your liking.

---

### Post by helix26 on 2007-06-13
Interesting - but alright, no uninstall of glib then.

In that case, how can I pass to configure the location of glib-2.12 so that I pass the glib test?

---

