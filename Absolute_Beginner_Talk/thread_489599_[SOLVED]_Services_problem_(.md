---
title: "[SOLVED] Services problem :("
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by spyros71 on 2007-07-01
Hello to everybody. I have the following problem: I get an error message Can't load HAL and when I try to set up  dbus with services I get the following:

spyros@Workstation:~$ services-admin

(services-admin:6487): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
6487: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
6487: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:6487): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
6487: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.
spyros@Workstation:~$ 

Can someone give me a hint?

Thanks in advance !!

---

### Post by computer_user_au on 2007-07-07
Hi, Had the same problem... check out this link: [http://ubuntuforums.org/showthread.php?t=289654&highlight=services-admin]("http://ubuntuforums.org/showthread.php?t=289654&highlight=services-admin")
Hope it helps...:)

---

### Post by spyros71 on 2007-07-07
Yeaaaa  !!!! It worked. Thank you very much. Ubuntu comunity is the BEST !!

---

