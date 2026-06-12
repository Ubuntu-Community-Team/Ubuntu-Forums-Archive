---
title: "Deluge Problem (iface?)"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by azizzle on 2007-12-12
Here is what I get:

desktop:~$ deluge
create proxy object
create iface
send to iface

Anybody?

Deluge won't open, even after I reboot. It just keeps coming up with this.

---

### Post by aktiwers on 2007-12-12
You could always try delete:
/home/username/.config/deluge

Change username to your own. Remeber the "." in config :)

---

### Post by eigenlambda on 2007-12-23
If you look at the source code to deluge (not that hard, it's in /usr/bin/deluge), it says:

```
 if not "org.deluge_torrent.Deluge" in dbus_objects:
        print "no existing Deluge session"
        start_deluge()
    else:
        ## This connects to the deluge interface
        print "create proxy object"
        proxy = bus.get_object('org.deluge_torrent.Deluge', '/org/deluge_torrent/DelugeObject')
        print "create iface"
        deluge_iface = dbus.Interface(proxy, 'org.deluge_torrent.Deluge')
        print "send to iface"

```

There's where your messages are coming from.  But what is dbus_objects?

```

if dbus_imported:
    bus = dbus.SessionBus()

    dbus_objects = dbus.Interface(bus.get_object('org.freedesktop.DBus', '/org/freedesktop/DBus'), 'org.freedesktop.DBus').ListNames()
```

So: deluge is using dbus to find other deluge instances, under the theory that nobody would want to run more than one deluge per gnome session.  In your case, there's probably an inactivated deluge process somewhere.  ps ax | grep deluge to find it, kill -9 to eliminate it.

hth.

---

