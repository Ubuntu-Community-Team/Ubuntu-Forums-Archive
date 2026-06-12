---
title: "Glib issues"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by disk11 on 2006-05-18
I'm trying to manually install a newer version of gnomad2, but when trying to setup atk for gtk+ to work, I get this:

```
checking for GLIB - version >= 2.5.7...
*** 'pkg-config --modversion glib-2.0' returned 2.11.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.11.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

```

I got confused with the update number scheme, I thought 2.8>2.10.

Anyway, I tried re-downloading the glib 2.8.3 source and doing "./configure; make uninstall" but that didn't work.  What do I need to do now to get all this working?

---

### Post by mynimal on 2006-05-18
I'm having this same problem, but with an older GLIB (2.5.7 - There's a 2.8.3 out..?). I can't remove GLIB because way, way too many programs depend on it. It's interwined with GTK I think.

I'm trying to install ATK so I can install GTK+ so I can install various applications, but jesus, I just keep running into problem after problem. I was having trouble with Cairo identifying FreeType, too..
[B]
Here's what you can do to fix your problem:[/B]

sudo gedit /usr/local/lib/pkgconfig/glib-2.0.pc

Change "Version" to 2.8.3

sudo gedit /usr/lib/pkgconfig/glib-2.0.pc

Do the same.

How did you update your GLIB? Could you give me a link to the download?

---

### Post by disk11 on 2006-05-18
[QUOTE=mynimal]I'm having this same problem, but with an older GLIB (2.5.7 - There's a 2.8.3 out..?). I can't remove GLIB because way, way too many programs depend on it. It's interwined with GTK I think.

I'm trying to install ATK so I can install GTK+ so I can install various applications, but jesus, I just keep running into problem after problem. I was having trouble with Cairo identifying FreeType, too..
[B]
Here's what you can do to fix your problem:[/B]

sudo gedit /usr/local/lib/pkgconfig/glib-2.0.pc

Change "Version" to 2.8.3

sudo gedit /usr/lib/pkgconfig/glib-2.0.pc

Do the same.

How did you update your GLIB? Could you give me a link to the download?[/QUOTE]

They are actually up to glib 2.11.  Source here: [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/)

It seems like I'm gonna have to uninstall the glib2.0 that came with the cd and resinstall packages as I need them, your fix didn't work.

---

### Post by disk11 on 2006-05-27
Bump, couldn't find much help in the IRC room and no response on Launchpad.

---

### Post by demauk on 2007-11-17
In case you are still having trouble with this, I suggest doing the following:

```
sudo apt-get install libglib2.0-0 libglib2.0-dev
```

That should install GLib 2.14.1 (which is indeed more recent than 2.8.3) and the -dev package will install the right config files that your script is looking for.

---

