---
title: "cant acess services`"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Blandust on 2007-03-14
I was configuring which apps would run at start up of ubuntu I guess i un-checked the wrong one now at startup I get a pop-up window, reading : "Failed to initialize HAL."
Also I cant access services anymore, it reads " The Configuration could not be loaded, you are not allowed to access system configuration."
How can I fix this? Thanks.

ahhhh sorry double post...

---

### Post by msaied on 2007-03-14
in the terminal type:
sudo services-admin 

inter password .
and activate the items you need in the services-admin window

---

### Post by Blandust on 2007-03-14
> (services-admin:9589): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
9589: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
9589: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:9589): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
9589: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

Hrmm, I tried that and entered my password and im giving the same message as If I were trying to directly open services, "The configuration could not be loaded, You are not allowed to access system config."

---

