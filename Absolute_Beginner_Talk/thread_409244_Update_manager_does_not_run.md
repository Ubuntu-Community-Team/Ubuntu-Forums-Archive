---
title: "Update manager does not run"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-14
I tried to run **update-manager -d** but update manager did not start.

Here is the output
```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 86, in ?
    app = UpdateManager(data_dir)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 300, in __init__
    self.setupDbus()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 440, in setupDbus
    '/org/freedesktop/UpdateManagerObject')
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 410, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 230, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.UpdateManager was not provided by any .service files

```

The update notifier does not run to. it is on my panel, but it does not run when I left click it. I tried to right click it and choose the "install all updates option" and it worked.

The only explanation for this that I can think of is my unsuccessful attempt to upgrade to Feisty. (See [this thread]("http://http://ubuntuforums.org/showthread.php?t=408315"))

After running the "install all updates," I saw that it was to install Feisty stuff like splash screens and all that, and I chose to continue installing all the updates so I'm downloading it now. Do you think it's okay?

What do you think may have caused the update manager not to run?

---

### Post by Seisen on 2007-04-16
Did it happen to install everything else when you were updating to fiesty.

---

