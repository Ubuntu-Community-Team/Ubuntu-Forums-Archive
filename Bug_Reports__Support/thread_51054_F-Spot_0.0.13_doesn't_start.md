---
title: "F-Spot 0.0.13 doesn't start"
date: 2005-07-22
forum: Bug Reports / Support
---

### Post by ubuntp on 2005-07-22
I just see F-Spot in the task bar for a few seconds, but no window opens or nothing.
Nevermind i compiled it myself and now it works.

Or does it? It doesn't show any PNGs  :-?

---

### Post by rwabel on 2005-07-23
[QUOTE=ubuntp]I just see F-Spot in the task bar for a few seconds, but no window opens or nothing.
Nevermind i compiled it myself and now it works.

Or does it? It doesn't show any PNGs  :-?[/QUOTE]
 what does happend, when you start f-spot (from ubuntu backport) from console? you will see some error message then

---

### Post by Kyral on 2005-08-03
F-Spot is broken. It depends on Mono but doesn't pull it in.

 ```
kyral@ArcadianUbuntu:~$ aptSh f-spot
Package: f-spot
Version: 0.0.13-0ubuntu1~5.04ubp1
Priority: optional
Section: gnome
Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Depends: libc6 (>= 2.3.2.ds1-4), libjpeg62, libsqlite0 (>= 2.8.15), libgphoto2-2 (>= 2.1.4), libexif10 (>= 0.5.1)
Architecture: i386
Filename: dists/hoary-backports/universe/binary-i386/f-spot_0.0.13-0ubuntu1~5.04ubp1_i386.deb
Size: 428688
MD5sum: b97eaad26b14e0e2fb76be999151a2fb
Description: personal photo management application
 F-Spot is meant to be an easy-to-use photo management
 application.  It allows for importing of your existing
 photo collections, tagging photos with identifiers,
 as well as doing simple edits of photos (e.g. rotating).
 .
 This application is still in its early stage of development.
installed-size: 1736

Package: f-spot
Priority: optional
Section: universe/gnome
Installed-Size: 1940
Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Architecture: i386
Version: 0.0.12-0ubuntu1
Depends: libc6 (>= 2.3.2.ds1-4), libjpeg62, libsqlite0 (>= 2.8.15), mono-jit (>= 1.0.5) | mono-mint (>= 1.0.5), libexif10, libgconf-cil (>= 1.0), libglade-cil (>= 1.0), libglib-cil (>= 1.0), libglib2.0-0 (>= 2.6.0), libgnome-cil (>= 1.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk-cil (>= 1.0), libgtk2.0-0 (>= 2.6.0), liblcms1 (>= 1.08-1), mono-assemblies-base (>= 1.0), libgphoto2-2 (>= 2.1.4), libexif10 (>= 0.5.1)
Filename: pool/universe/f/f-spot/f-spot_0.0.12-0ubuntu1_i386.deb
Size: 531774
MD5sum: f8d5f19f8798b0a2413740202eee7566
Description: personal photo management application
 F-Spot is meant to be an easy-to-use photo management
 application.  It allows for importing of your existing
 photo collections, tagging photos with identifiers,
 as well as doing simple edits of photos (e.g. rotating).
 .
 This application is still in its early stage of development.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by Davidios on 2005-09-02
When I start f-spot in the console this appear:
```
david@linux:~$ f-spot

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00213> PhotoStore:Query (.Tag[] tags, .DateRange range)
in <0x00029> FSpot.PhotoQuery:.ctor (.PhotoStore store)
in <0x005f3> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)
``` 

Then F-spot starts but in a second it closes. :?

---

### Post by Davidios on 2005-09-03
Nobody?

---

### Post by Davidios on 2005-09-03
C'mon, it's important :(

---

### Post by Davidios on 2005-09-03
Ok, I've got it!

> Hi all,

I just wanted to note a crash I've encountered:
If you rename the 'Hidden' tag in F-Spot to anything else, and quit
the program, when you come back next time the program will crash right
after showing the main window (without any controls inside it) The
error i get is:
--------------------------------
(these first two lines repeat many times before showing the Unhandled Exception)
(f-spot:6105): GLib-CRITICAL **: g_key_file_add_group: assertion
`g_key_file_loo kup_group_node (key_file, group_name) == NULL' failed

Unhandled Exception: System.NullReferenceException: Object reference
not set to an instance of an object
in <0x00213> PhotoStore:Query (.Tag[] tags, .DateRange range)
in <0x00029> FSpot.PhotoQuery:.ctor (.PhotoStore store)
in <0x00630> MainWindow:.ctor (.Db db)
in <0x00330> Driver:Main (System.String[] args)
--------------------------------
And the only way to make the program work again i've found is to
delete ~/.gnome2/f-spot/photos.db
So if you're going to reproduce the bug, backup the file or you'll
loose your entire photo collection. Renaming the rest of the tags
seems to work fine.
I'm using Mono 1.1.8.3 from nrpms on a Fedora 4 system, and I'm using
a F-Spot copy checked-out from the main gnome cvs server as of
yesterday night.
Hope the info is useful

---

