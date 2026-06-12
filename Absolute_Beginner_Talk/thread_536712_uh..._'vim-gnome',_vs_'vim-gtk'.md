---
title: "uh... 'vim-gnome', vs 'vim-gtk'?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by jf/ on 2007-08-28
I'm not too sure about 'GNOME2 GUI', vs 'GTK2 GUI', but could somebody enlighten me here? What is the difference between the 2?

---

### Post by olejorgen on 2007-08-28
I'd guess that gnome-gtk does not depend on any *gnome* libraries. I'm not entirely sure what in gnome vim-gnome uses though.

So if you're using ubuntu, go for the gnome version, if you're using xbuntu go for gtk2.

---

### Post by jf/ on 2007-08-28
> **olejorgen said:**
> I'd guess that gnome-gtk does not depend on any *gnome* libraries. I'm not entirely sure what in gnome vim-gnome uses though.

So if you're using ubuntu, go for the gnome version, if you're using xbuntu go for gtk2.
:) thanks. That's a very intelligent guess!! I guess you're probably right - although I would definitely love to be able to know just exactly what within gnome vim-gnome depends on....

---

### Post by olejorgen on 2007-08-28
Well, you can see which packages it depends on, but it might not tell you very much :)

apt-cache show vim-gnome

---

### Post by jf/ on 2007-08-28
:) thanks, but you're right about that one!!! It doesn't tell me anything much...

---

### Post by mcduck on 2007-08-28
That was interesting question :)

Even when this will become a long post, here are descriptions to packages that are listed as dependencies for vim-gnome but not for vim-gtk:

_**libart-2.0-2 (>= 2.3.16)**_
 Library of functions for 2D graphics - runtime files
 A library of functions for 2D graphics supporting a superset of the
 PostScript imaging model, designed to be integrated with graphics, artwork,
 and illustration programs. It is written in optimized C, and is fully
 compatible with C++. With a small footprint of 10,000 lines of code, it is
 especially suitable for embedded applications.
 
_**libbonobo2-0 (>= 2.15.0)**_
 Bonobo CORBA interfaces library
 Bonobo is a set of language and system independent CORBA interfaces
 for creating reusable components, controls and creating compound
 documents.
 .
 The Bonobo distribution includes a Gtk+ based implementation of the
 Bonobo interfaces, enabling developers to create reusable
 components and applications that can be used to form more complex
 documents.
 
_**libbonoboui2-0 (>= 2.15.1)**_
The Bonobo UI library
 This package contains the Bonobo UI library.
 .
 This package is a part of GNOME2

_**libgconf2-4 (>= 2.13.5)**_
 GNOME configuration database system (shared libraries)
 GConf is a configuration database system for storing application
 preferences. It supports default or mandatory settings set by the
 administrator, and changes to the database are instantly applied to all
 running applications. It is written for the GNOME desktop but doesn't
 require it.
 .
 This package contains the shared libraries and the GConf daemon.

_**libgnome-keyring0 (>= 0.7.1)**_
 GNOME keyring services library
 gnome-keyring is a daemon in the session, similar to ssh-agent,
 and other applications can use it to store passwords and other
 sensitive information.
 .
 The program can manage several keyrings, each with its own master
 password, and there is also a session keyring which is never stored to
 disk, but forgotten when the session ends.
 .
 This package contains shared libraries for GNOME.

_**libgnome2-0 (>= 2.14.1)**_
The GNOME 2 library - runtime files
 This package contains the shared library for the base GNOME library
 functions.

_**libgnomecanvas2-0 (>= 2.11.1)**_
 A powerful object-oriented display - runtime files
 The canvas widget is a powerful and extensible object-oriented display
 engine. A GnomeCanvasItem is a GtkObject representing some element of the
 display, such as an image, a rectangle, an ellipse, or some text. You can
 refer to this architecture as structured graphics; the canvas lets you deal
 with graphics in terms of items, rather than an undifferentiated grid of
 pixels.

_**libgnomeui-0 (>= 2.17.1)**_
The GNOME 2 libraries (User Interface) - runtime files
 This package contains the shared library for the base GNOME library
 functions (User Interface functions)

_**libgnomevfs2-0 (>= 1:2.17.90)**_
GNOME virtual file-system (runtime libraries)
 GNOME VFS is the GNOME virtual file system. It is the foundation of the
 Nautilus file manager. It provides a modular architecture and ships with
 several modules that implement support for file systems, http, ftp and others.
 It provides a URI-based API, a backend supporting asynchronous file
 operations, a MIME type manipulation library and other features.
 .
 This package contains the runtime libraries, the daemon, and the
 default modules.

_**liborbit2 (>= 1:2.14.1)**_
 libraries for ORBit2 - a CORBA ORB
 ORBit2 is a high-performance CORBA (Common Object Request Broker
 Architecture) ORB (Object Request Broker). It allows programs to send
 requests and receive replies from other programs, regardless of the
 locations of the two programs. CORBA is an architecture that enables
 communication between program objects, regardless of the programming
 language they're written in or the operating system they run on.
 .
 This package contains the run-time libraries used by ORBit2-based
 applications.

_**libpopt0 (>= 1.10)**_
 lib for parsing cmdline parameters
 Popt was heavily influenced by the getopt() and getopt_long() functions,
 but it allows more powerful argument expansion. It can parse arbitrary
 argv[] style arrays and automatically set variables based on command
 line arguments. It also allows command line arguments to be aliased via
 configuration files and includes utility functions for parsing arbitrary
 strings into argv[] arrays using shell-like rules.
 .
 This package contains the runtime library and locale data.

...

Based on those, I'd say that vim-gnome has support for network filesystems using Gnome VFS, storing settings in gconf database and storing passwords (or something) with Gnome Keyring. Probably there are also some improvements in the user interface.

---

