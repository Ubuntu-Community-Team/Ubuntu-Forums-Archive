---
title: "update manager broken"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by veritas366 on 2006-02-14
Actually lots of things broke from when I was trying to tweak my desktop following directions in one of the customization threads.  Update manager gives me this:

```
ty@ubuntu:~ $ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 27, in ?
    import gtk
ImportError: No module named gtk
ty@ubuntu:~ $

```

Surely that got borked with my silly attempts to get composite windows.  However, I can't figure out how to get it back.  Lots of packages with gtk in them but none seem to be the right one.  Or is there a line in some configuration file somewhere that isn't right?  Please help...I know I can do it via apt-get but I NEVER remember.  Plus, I think the GTK prob is causing other issues.

---

### Post by davmac on 2006-02-15
It is not a problem I've faced myself, but if I was in the same position I'd use synaptics or apt-get to remove and then reinstall update-manager, and hope that it would reinstall the relevant gtk stuff with it.

I wouldn't try it without a backup through!

Hope this helps,

Dave Mac

---

### Post by veritas366 on 2006-02-15
[QUOTE=davmac]It is not a problem I've faced myself, but if I was in the same position I'd use synaptics or apt-get to remove and then reinstall update-manager, and hope that it would reinstall the relevant gtk stuff with it.

I wouldn't try it without a backup through!

Hope this helps,

Dave Mac[/QUOTE]

Actually, I did try that and it didn't work.

---

### Post by davmac on 2006-02-15
OK. If I open up a terminal and type in "dpkg -l | grep gtk" to list all of the packages that reference gtk I get;

```
ii  ardour-gtk-i686                        0.9beta29-5ubuntu1                             digital audio workstation (graphical gtk interfa
ii  firestarter                            1.0.3-1.1ubuntu1                               gtk program for managing and observing your fire
ii  gdk-imlib1                             1.9.14-16.2ubuntu4                             imaging library for use with gtk (using libpng2)
ii  gftp-gtk                               2.0.18-10                                      X/GTK+ FTP client
ii  graveman                               0.3.12-4-2                                     graphical tool to burn dvd and cd, gtk based
ii  gstreamer0.8-gtk                       0.8.11-0ubuntu5                                GdkPixbuf decoder plugin for GStreamer
ii  gtk2-engines-clearlooks                2.6.5-0ubuntu2                                 the ClearLooks theme engine for GTK+ 2.x
ii  gtk2-engines-crux                      2.6.5-0ubuntu2                                 the Crux theme engine for GTK+ 2.x
ii  gtk2-engines-industrial                2.6.5-0ubuntu2                                 'industrial' theme for GTK+ 2.x
ii  gtk2-engines-lighthouseblue            2.6.5-0ubuntu2                                 LighthouseBlue theme for GTK+ 2.x
ii  gtk2-engines-mist                      2.6.5-0ubuntu2                                 flat theme for GTK+ 2.x
ii  gtk2-engines-pixbuf                    2.8.6-0ubuntu2.1                               Pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-redmond95                 2.6.5-0ubuntu2                                 Windows-like theme for GTK+ 2.x
ii  gtk2-engines-smooth                    2.6.5-0ubuntu2                                 Smooth Engine for GTK+ 2.x
ii  gtk2-engines-thinice                   2.6.5-0ubuntu2                                 the ThinIce theme engine for GTK+ 2.x
ii  gtk2-engines-xfce                      2.3.0cvs20050306-2                             Gtk+-2.0 theme engine for Xfce
ii  gtkhtml3.8                             3.8.1-0ubuntu1                                 HTML rendering/editing library - bonobo componen
ii  libgdk-pixbuf2                         0.22.0-8ubuntu0.1                              The GdkPixBuf image library, gtk+ 1.2 version
ii  libgtk-canvas1                         0.1.1-7                                        port of GNOME Canvas back to gtk+
ii  libgtk-cil                             1.0.10-0ubuntu4                                CLI binding for the Gtk+ toolkit
ii  libgtk-perl                            0.7009-3ubuntu1                                Perl module for the gtk+ library
ii  libgtk-pixbuf-perl                     0.7009-3ubuntu1                                Perl module for the gdkpixbuf library
ii  libgtk1.2                              1.2.10-17build1                                The GIMP Toolkit set of widgets for X
ii  libgtk1.2-common                       1.2.10-17build1                                Common files for the GTK+ library
ii  libgtk2-perl                           1.100-1                                        Perl interface to the 2.x series of the Gimp Too
ii  libgtk2-ruby                           0.13.0-2ubuntu1                                GTK+ bindings for the Ruby language
ii  libgtk2.0-0                            2.8.6-0ubuntu2.1                               The GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.8.6-0ubuntu2.1                               The programs for the GTK+ graphical user interfa
ii  libgtk2.0-cil                          2.3.92-0ubuntu1                                CLI binding for the Gtk+ toolkit 2.0, unstable v
ii  libgtk2.0-common                       2.8.6-0ubuntu2.1                               Common files for the GTK+ graphical user interfa
ii  libgtkhtml2-0                          2.6.3-1                                        HTML rendering/editing library - runtime files.
ii  libgtkhtml3.8-15                       3.8.1-0ubuntu1                                 HTML rendering/editing library - runtime files
ii  libgtkmm-2.4-1c2                       2.8.0-0ubuntu1                                 C++ wrappers for GTK+ 2.4 (shared libraries)
ii  libgtkmm1.2-0c2                        1.2.10-7ubuntu2                                C++ wrappers for GTK+ 1.2 (shared libraries)
ii  libgtksourceview-common                1.4.2-0ubuntu1                                 common files for the GTK+ syntax highlighting wi
ii  libgtksourceview1.0-0                  1.4.2-0ubuntu1                                 shared libraries for the GTK+ syntax highlightin
ii  libgtkspell0                           2.0.10-2build1                                 a spell-checking addon for GTK's TextView widget
ii  libwxgtk2.4-1                          2.4.4.1ubuntu1                                 wxWindows Cross-platform C++ GUI toolkit (GTK+ r
ii  libwxgtk2.6-0                          2.6.1.1.1ubuntu2                               wxWidgets Cross-platform C++ GUI toolkit (GTK+ r
ii  python-gtk2                            2.8.1-0ubuntu2                                 Python bindings for the GTK+ widget set
ii  python2.4-gtk2                         2.8.1-0ubuntu2                                 Python bindings for the GTK+ widget set
ii  vim-gtk                                6.3-078+1ubuntu3                               Vi IMproved - GTK2 Version

```

If you do the same, are there obvious things missing?

Dave Mac

---

### Post by veritas366 on 2006-02-15
> If you do the same, are there obvious things missing?

Nothing about this is obvious to me.  I have no idea what is supposed to be in there.  That's why I'm posting in this forum.  Here's the output:

```
ii  gdk-imlib1                             1.9.14-16.2ubuntu4 imaging library for use with gtk (using libp
ii  gstreamer0.8-gtk                       0.8.11-0ubuntu5 GdkPixbuf decoder plugin for GStreamer
ii  gtk-engines-geramik-data               0.26-2.1 Geramik GTK Theme bitmaps
ii  gtk2-engines-clearlooks                2.6.5-0ubuntu2 the ClearLooks theme engine for GTK+ 2.x
ii  gtk2-engines-crux                      2.6.5-0ubuntu2 the Crux theme engine for GTK+ 2.x
ii  gtk2-engines-geramik                   0.26-2.1 Geramik GTK2.x Theme
ii  gtk2-engines-gtk-qt                    0.60-1ubuntu5 Makes your GTK 2 apps look like Qt ones
ii  gtk2-engines-highcontrast              2.6.5-0ubuntu2 High contrast GTK+ 2.x theme engine
ii  gtk2-engines-industrial                2.6.5-0ubuntu2 'industrial' theme for GTK+ 2.x
ii  gtk2-engines-lighthouseblue            2.6.5-0ubuntu2 LighthouseBlue theme for GTK+ 2.x
ii  gtk2-engines-magicchicken              1.1.1-7 Magic Chicken themes for GTK+ 2.x
ii  gtk2-engines-metal                     2.6.5-0ubuntu2 Metallic theme for GTK+ 2.x
ii  gtk2-engines-mist                      2.6.5-0ubuntu2 flat theme for GTK+ 2.x
ii  gtk2-engines-pixbuf                    2.8.6-0ubuntu2.1 Pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-qtpixmap                  0.28-1.1 QtPixmap GTK2.x theming engine
ii  gtk2-engines-redmond95                 2.6.5-0ubuntu2 Windows-like theme for GTK+ 2.x
ii  gtk2-engines-smooth                    2.6.5-0ubuntu2 Smooth Engine for GTK+ 2.x
ii  gtk2-engines-spherecrystal             0.7-10 A blue vector theme for GTK+ 2.x
ii  gtk2-engines-thinice                   2.6.5-0ubuntu2 the ThinIce theme engine for GTK+ 2.x
ii  gtk2-engines-wonderland                1.0-2.2 Wonderland theme for GTK+ 2.0
ii  gtk2-engines-xfce                      2.3.0cvs20050306-2 Gtk+-2.0 theme engine for Xfce
ii  gtkhtml3.2                             3.2.3ubuntu1-1ubuntu1 HTML rendering/editing library - bonobo comp
ii  gtkhtml3.6                             3.6.2-1 HTML rendering/editing library - bonobo comp
ii  gtkhtml3.8                             3.8.1-0ubuntu1 HTML rendering/editing library - bonobo comp
ii  gtkodbcconfig0                         2.2.11-8ubuntu1 GTK-based ODBC configuration library
ii  libgdk-pixbuf2                         0.22.0-8ubuntu0.1 The GdkPixBuf image library, gtk+ 1.2 versio
ii  libgnorbagtk0                          1.4.2-20 GNOME CORBA services (Gtk bindings)
ii  libgtk-cil                             1.0.10-0ubuntu4 CLI binding for the Gtk+ toolkit
ii  libgtk1.2                              1.2.10-17build1 The GIMP Toolkit set of widgets for X
ii  libgtk1.2-common                       1.2.10-17build1 Common files for the GTK+ library
ii  libgtk2-perl                           1.100-1 Perl interface to the 2.x series of the Gimp
ii  libgtk2-ruby                           0.13.0-2ubuntu1 GTK+ bindings for the Ruby language
ii  libgtk2.0-0                            2.8.6-0ubuntu2.1 The GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.8.6-0ubuntu2.1 The programs for the GTK+ graphical user int
ii  libgtk2.0-cil                          2.3.92-0ubuntu1 CLI binding for the Gtk+ toolkit 2.0, unstab
ii  libgtk2.0-common                       2.8.6-0ubuntu2.1 Common files for the GTK+ graphical user int
ii  libgtkglext1                           1.0.6-2ubuntu5 OpenGL Extension to GTK (shared libraries)
ii  libgtkhtml2-0                          2.6.3-1 HTML rendering/editing library - runtime fil
ii  libgtkhtml3.0-4                        3.0.10-1 HTML rendering/editing library - runtime fil
ii  libgtkhtml3.2-11                       3.2.3ubuntu1-1ubuntu1 HTML rendering/editing library - runtime fil
ii  libgtkhtml3.6-18                       3.6.2-1 HTML rendering/editing library - runtime fil
ii  libgtkhtml3.8-15                       3.8.1-0ubuntu1 HTML rendering/editing library - runtime fil
ii  libgtkmm-2.4-1c2                       2.8.0-0ubuntu1 C++ wrappers for GTK+ 2.4 (shared libraries)
ii  libgtksourceview-common                1.4.2-0ubuntu1 common files for the GTK+ syntax highlightin
ii  libgtksourceview1.0-0                  1.4.2-0ubuntu1 shared libraries for the GTK+ syntax highlig
ii  libgtkspell0                           2.0.10-2build1 a spell-checking addon for GTK's TextView wi
rc  openoffice.org-gtk-gnome               1.1.3-8ubuntu2.3 Gtk UI Plugin and GNOME File Picker for Open
ii  pioneers-server-gtk                    0.9.23-1 computer version of the settlers of Catan bo
ii  python-gtk2                            2.8.1-0ubuntu2 Python bindings for the GTK+ widget set
ii  python2.4-gtk2                         2.8.1-0ubuntu2 Python bindings for the GTK+ widget set
ii  unison-gtk                             2.13.16-2~breezy1 A file-synchronization tool for Unix and Win
ty@ubuntu:~ $

```
 Can you see something missing that should be there?  What should be there for the update manager.  Also, I tried the free Cedega trial and it behaved similarly but no error messages.  I try to install a game, the install shield goes up and then it freezes.  Maybe not related at all, but in case that info gives a clue.

Thanks for helping.

---

### Post by LordYama on 2006-02-16
I'm having the same problem. Aptitude (which is better than apt-get anyway) appears to be working.

---

### Post by souteneur3190 on 2006-02-16
ok i know this is VERY off topic but im deperate

any1 with there user/share/pixmaps folder untouched please send it to me...i deleted mine.  we can direct connect or something, my s/n for gaim is souteneur3190, please help

---

### Post by soundray on 2007-06-01
I had the same problem and found that it could be fixed with
```

sudo apt-get --reinstall install python2.5-gtk2 python-glade2 python-gconf
```

Hope that helps

soundray

---

