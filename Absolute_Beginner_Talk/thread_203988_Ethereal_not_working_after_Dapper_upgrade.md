---
title: "Ethereal not working after Dapper upgrade"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Tom Fury on 2006-06-26
If there is a better place for this question, please point me there.  I have an IBM T42 laptop that had Breezy on it and I never had a problem running ethereal.  I upgraded it to Dapper and keep getting the following errors.  I thought that they may be a issue with the upgrade, so I reinstalled Dapper from scratch and still keep getting these errors.  Ethereal will run for a short while and then just stop capturing packets.  I get these errors on the terminal that I sudo ethereal from.  Here are the errors:

(ethereal:6056): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkProgressBar'

(ethereal:6056): Gtk-CRITICAL **: gtk_progress_bar_update: assertion `GTK_IS_PROGRESS_BAR (pbar)' failed

(ethereal:6056): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkLabel'

(ethereal:6056): Gtk-CRITICAL **: gtk_label_set_text: assertion `GTK_IS_LABEL (label)' failed

---

### Post by Tom Fury on 2006-06-29
It looks like it is [a bug in ethereal.]("http://bugs.ethereal.com/bugzilla/show_bug.cgi?id=895")  Since it is the same version and it worked in Breezy, I wonder what is different in Dapper that made this not work after the upgrade.

---

