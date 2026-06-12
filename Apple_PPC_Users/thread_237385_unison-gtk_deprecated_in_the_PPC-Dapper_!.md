---
title: "unison-gtk deprecated in the PPC-Dapper ?!"
date: 2006-08-16
forum: Apple PPC Users
---

### Post by blatny on 2006-08-16
Hi,
I've been testing dual boot Dapper/Tiger on my PowerBook G4 for about two weeks. I've been surprised how mature the Ubuntu Dapper Deskop is in comparison to the commercial Mac OS X. And I fairly don't understand why people still pay for this Windoze/KillBill thing. My best regards to Mark Shuttleworth and the team. Money well spent.

Well, now back to the problem. I have installed the unison and unison-gtk both from the Universe Repositories. The command line "unison" seems to work, however, if I try to start up the GUI version "unison-gtk" I am getting a very long list of errors. Reinstallation doesn't help and the older version 2.9.1 shows the same error as well. Anyone gets this?!


$ unison-gtk
Uncaught exception Gtk.Error("GtkMain.init: initialization failed\nml_gtk_init: initialization failed")

(unison-gtk:6311): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(unison-gtk:6311): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(unison-gtk:6311): GLib-GObject-WARNING **: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'

(unison-gtk:6311): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(unison-gtk:6311): Gdk-CRITICAL **: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_set_attributes: assertion `layout != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_set_alignment: assertion `layout != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_set_width: assertion `layout != NULL' failed

(unison-gtk:6311): Pango-CRITICAL **: pango_layout_get_extents: assertion `layout != NULL' failed

(unison-gtk:6311): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(unison-gtk:6311): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(unison-gtk:6311): Gtk-CRITICAL **: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed

(unison-gtk:6311): Gtk-WARNING **: Invalid icon size 6


(unison-gtk:6311): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
Segmentation fault

---

### Post by DrBubba on 2006-08-17
Hmm,  I just installed unison-gtk to see if I could reproduce this on my G4 powerbook - with no luck.  Looking at the error messages it looks like there could be something wrong with one of the dependencies.  Apt-cache gave the following:

victor@bubba:~$ apt-cache depends unison-gtk
unison-gtk
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libexpat1
  Depends: libfontconfig1
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libpango1.0-0
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxrandr2
  Recommends: ssh-askpass
    gtk-led-askpass
    ssh-askpass-fullscreen
    ssh-askpass-gnome
 |Recommends: <ssh-client>
    ssh-krb5
    openssh-client
  Recommends: openssh-client
  Conflicts: unison-gtk

The last "Conflicts" line is for versions < 2.9.1-3 BTW.  You can get the actual version numbers either by searching for unison in synaptic or by typing "apt-cache show unison-gtk" (among other methods).  I suspect, from the errors that you've got that one of the dependencies isn't quite right - it could be that its one of those.  I'm not much of a programmer these days, but I'd suspect one or more of libgtk2.0-0, libpango1.0-0 or libxfixes3.  You might check to see if the versions match - though all other things being equal they should.  Hope this helps.

V.

---

### Post by DrBubba on 2006-08-17
BTW, by "no-luck" I mean that it works fine for me.  Sorry about that, I'm kind of jetlagged this morning.

V.

---

