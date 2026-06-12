---
title: "jockey-gtk issues"
date: 2012-10-17
forum: Apple Hardware Users
---

### Post by cinenate on 2012-10-17
Hi There. I've searched around and could not find any soltuions to this issue. When I run
jockey-gtk or go to "System Settings", "Additional Drivers" I get this error

> (jockey-gtk:3281): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:3281): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
Exception in thread thread_call_progress_dialog:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Python.IOError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 173, in detect
    self.hardware = detection.get_hardware()
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 905, in get_hardware
    result = _get_modaliases()
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 659, in _get_modaliases
    modalias = open(os.path.join(path, 'modalias')).read().strip()
IOError: [Errno 19] No such device


Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 274, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 819, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 212, in available
    handler_names = self.handlers.keys()
AttributeError: 'Backend' object has no attribute 'handlers'
I have tried removing jockey-gtk, updating the list, and reinstalling. That has not solved the issue. I am running the newest version, fully updated, on a PowerMac G5.

Thanks!

---

### Post by gregbrown on 2012-10-19
I have the same problem on an HP. Installed 12.04.1 from usb. Updated software using automatic update. Installed recommended Nvidia proprietary driver. After system login the screen would show three bars of garbage in lower half.  System would not respond. I reinstalled and updated software automatically again. I have not reinstalled recommended Nvidia driver. I got an error from  jockey-gtk and reported it using the automatic feature. When I run sudo jockey-gtk I get this response:

(jockey-gtk:2718: Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:2718: Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

So, I'm guessing this isn't an Apple-only problem.

---

### Post by mlaxton on 2013-07-19
I've got the same issue on a G5.  Every find a resolution?

---

