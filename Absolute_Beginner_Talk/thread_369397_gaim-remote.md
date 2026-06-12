---
title: "gaim-remote"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by xtephan on 2007-02-24
Hello!
i try to use gaim-remote but it crashes all the time

Introspect error: The name net.sf.gaim.GaimService was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/gaim-remote", line 193, in ?
    print execute(arg)
  File "/usr/bin/gaim-remote", line 140, in execute
    data = dbus.Interface(obj, "org.freedesktop.DBus.Introspectable").\
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name net.sf.gaim.GaimService was not provided by any .service files

had anyone this kind of problem before?
thanks

---

### Post by energiya on 2007-02-25
Have you compiled your Gaim from source or used a repository? If you used a repo, I suggest trying to compile.
After a quick look I see "net.sf.gaim.GaimService" defined in "dbus-gaim.h"
> 
#define DBUS_SERVICE_GAIM      "net.sf.gaim.GaimService"

I can't give more help, as I never experienced any similar problem. Anyway, my advice is to compile from source. That way you may have better control on what is happening.

---

