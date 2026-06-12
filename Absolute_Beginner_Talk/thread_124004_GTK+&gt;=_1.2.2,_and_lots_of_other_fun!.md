---
title: "GTK+&gt;= 1.2.2, and lots of other fun!"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-31
Trying to install a plugin for XMMS, it said I needed to install GTK+>= 1.2.2, and so I did, and it took an age....

Now it's saying...
> *** 'gtk-config --version' returned 1.2.2, but GTK+ (1.2.10)
*** was found! If gtk-config was correct, then it is best
*** to remove the old version of GTK+. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If gtk-config was wrong, set the environment variable GTK_CONFIG
*** to point to the correct copy of gtk-config, and remove the file config.cache*** before re-running configure

What should I do, guys?

Thanks

---

### Post by SectionThree on 2006-01-31
Go into Synaptic and find GTK+ 1.2.10. Mark it for removal and hit apply. Wait until the resulting dialog says "You can close the window now." Try installing your plugin again.

---

### Post by Jimmey on 2006-01-31
There's no entry for GTK+ anywhere in the package manager...
I fiddled with the GTK libs, but STILL nothing?
Please help :(

---

### Post by az on 2006-01-31
1.2.10 is greater than 1.2.2.  The libgtk1.2-dev that ships with ubuntu should work fine.  Either ignore the warning, change the config or find a different source for your plugin.

---

### Post by Jimmey on 2006-01-31
So I needn't install anything to get this working - The components it asks for are already there, on the standard Ubuntu installation?

Change what config? How'd I do that?

---

### Post by az on 2006-01-31
[QUOTE=Jimmey]So I needn't install anything to get this working - The components it asks for are already there, on the standard Ubuntu installation?
[/QUOTE]

No.  Install libgtk1.2-dev.

[QUOTE=Jimmey]
Change what config? How'd I do that?[/QUOTE]

"*** If gtk-config was wrong, set the environment variable GTK_CONFIG
*** to point to the correct copy of gtk-config, and remove the file config.cache*** before re-running configure"

---

### Post by Jimmey on 2006-01-31
And yet, I'm still lacking a sense of enlightenment...Sorry, I'm a bit of a newbie..

---

### Post by az on 2006-01-31
To compile stuff, you need the toolchain (build-essential), the sourcecode (the tarball) and any requirements the code needs to link against (read the README and install any -dev packages.  In this case, you need the gtk1.2 libraries, so you install libgtk1.2-dev)

That is in general terms.  I don't even know what you are trying to compile.  It does say that you require GTK+>= 1.2.2 which is satisfied by libgtk1.2-1.2.10.

---

