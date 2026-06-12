---
title: "[need help] driconf error"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by andekhi on 2007-04-11
i tried to run driconf, but i had these errors :
```

root@Admin:/media/sda5/Gudang/Linux# driconf
/var/lib/python-support/python2.4/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Error: Couldn't open display
/usr/lib/python2.4/site-packages/driconf.py:55: Warning: invalid (NULL) pointer instance
  gtk.BUTTONS_OK, str(problem))
/usr/lib/python2.4/site-packages/driconf.py:55: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  gtk.BUTTONS_OK, str(problem))
/usr/lib/python2.4/site-packages/driconf.py:55: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  gtk.BUTTONS_OK, str(problem))
/usr/lib/python2.4/site-packages/driconf.py:55: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  gtk.BUTTONS_OK, str(problem))
/usr/lib/python2.4/site-packages/driconf.py:55: Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
  gtk.BUTTONS_OK, str(problem))
/usr/lib/python2.4/site-packages/driconf.py:56: GtkWarning: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_new: assertion `context != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_set_text: assertion `layout != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_set_attributes: assertion `layout != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_set_alignment: assertion `layout != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_set_width: assertion `layout != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: PangoWarning: pango_layout_get_extents: assertion `layout != NULL' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: GtkWarning: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: GtkWarning: Invalid icon size 6

  dialog.run()
/usr/lib/python2.4/site-packages/driconf.py:56: GtkWarning: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
  dialog.run()
Segmentation fault (core dumped)

```

any suggestion, i'm newbie in ubuntu, actually this is my firstime using linux other than redhat fedora, thx in advance

---

### Post by andekhi on 2007-04-11
anyone? i have these problem to play some games (with soya 3d), someone suggest me to use driconf to adjust max pixel. thx in advanced

---

