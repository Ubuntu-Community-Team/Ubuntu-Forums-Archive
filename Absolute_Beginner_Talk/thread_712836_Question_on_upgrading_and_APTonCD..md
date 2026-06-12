---
title: "Question on upgrading and APTonCD."
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by chrispche on 2008-03-02
When the time comes for me to upgrade from Gutsy to Heron. Will my backup APTonCD still work? Or shall I wait till I do the upgrade and make an APTonCD backup then. I think I'll be using the LTS version from then on. As I have heard through the grapevine Ubuntu are making LTS to LTS upgrades available.

Thanks.

---

### Post by aysiu on 2008-04-02
If APTonCD uses packages from Gutsy, then those packages may not work on Hardy, as they are older versions of the software.

---

### Post by DarkDemonNT on 2008-04-25
I install APTonCD, but I can't restore from *.iso file.
When I run aptoncd from terminal, and i chose restore, and click Load:
> Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/APTonCD/restore/restoreWindow.py", line 209, in on_btnLoadFrom
    drives = bus.get_devices()
  File "/usr/lib/python2.5/site-packages/APTonCD/core/dbus_helper.py", line 38, in get_devices
    if vol.GetPropertyBoolean("volume.is_disc") and vol.GetPropertyBoolean("volume.disc.has_data"):
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "(unset)" member "GetPropertyBoolean" error name "(unset)" destination ":1.5")
Could you help me?
I'm using hardy heron RC

Sorry about my English.
I hope you understand.

---

### Post by rogerdean on 2008-05-31
there's a fix for aptoncd coming. in the meantime you can install the unreleased fix from 

[http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb](http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb)

---

### Post by minhaaj on 2008-07-07
It works! i am using hardy and its awesome. Problem i have is it won't make incremental back ups. I also would like to see aptoncd guys to make a back up for whole system that would boot off and install ubuntu with all your configs. That would be awesome. i can't back up nothing :(

---

