---
title: "Deluge Plugin Preferences Greyed Out"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by jusmurph on 2007-11-22
I can't edit any of the preferences of any plugin, the preference button is simply greyed out.

Also down the bottom of the main window, there is only the details tab, no files tab etc.

Thanks in advance

---

### Post by drworm01 on 2007-12-09
I'm having a similar problem. I can't access the Preferences menus in Deluge anymore. When I run it through Terminal and hit the Preferences button, I get this response:

```
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 697, in show_preferences_dialog_clicked
    self.show_preferences_dialog()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 691, in show_preferences_dialog
    preferences_dialog.show(self, self.window)
  File "/var/lib/python-support/python2.5/deluge/dialogs.py", line 98, in show
    self.glade.get_widget("finished_path_button").set_filename(self.preferences.get("default_finished_path"))
TypeError: GtkFileChooser.set_filename() argument 1 must be string, not None


```

Can anyone tell me how to fix that? Thanks.

---

