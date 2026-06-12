---
title: "[SOLVED] Massive problems with the gnome panel"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2008-04-09
My gnome panel keeps crashing after logon, so it will disappear as if I've run a "killall" command, then slide back into view. It does this several times before completely disappearing for the whole session. Restarting X doesn't do anything.

Starting it in the terminal gives me this error:

> (gnome-panel:11086): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(gnome-panel:11086): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:11086): Gtk-CRITICAL **: gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault


EDIT: Never mind, update fixed it.

---

