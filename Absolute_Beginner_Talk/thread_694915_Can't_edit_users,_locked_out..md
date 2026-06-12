---
title: "Can't edit users, locked out."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Kosika on 2008-02-12
Hello. I've kind of "locked my self out". I've been playing around a bit with ubuintu now, and have set up an ftp server etc.
Now the problem. I can edit users and groups. I just get the message "You are not allowed to access the system configuration."
I've tried to do```
 sudo gksu users-admin
``` but I still get the same error.
What can i do to be able to edit users and groups again? There's also other things i can't acces.
The account I'm using is the one I've created at install. and the only one I have ever logged in with (exept for ftp). I cannot recall that I have edited my own account setting some way, perhaps just changed group.
Please help me. tell me if you need more info.
Thanks!

---

### Post by taurus on 2008-02-12
What's the output of this command?

```
id
```

---

### Post by emarkd on 2008-02-12
Run:

```
groups yourusername
```

to see which groups you're a member of.

---

### Post by Kosika on 2008-02-13
Hi., thanks for the replys.
Here are the outputs you requested
```

hostile@hostile-desktop:~$ id
uid=1000(hostile) gid=1000(hostile) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(hostile)

```
```
hostile@hostile-desktop:~$ groups hostile
hostile : hostile adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin

```

Thanks!

---

### Post by taurus on 2008-02-13
What happens when you run these two commands?

```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  You don't need to include both _sudo_ and _gksu_ at the same time if you want to open an app with root privilege since both behave the same whereas su is for terminal while gksu is for GUI app.

---

### Post by sigge on 2008-02-13
> **Kosika said:**
> Hello.
I've tried to do```
 sudo gksu users-admin
``` but I still get the same error.
Thanks!

Ok. The code should be:
```
gksu users-admin
``` *without* the sudo... :)

Hope it helps!

---

### Post by Kosika on 2008-02-13
Hi thanks again for the replies.
The sudo apt-get command are succefull. it updates some stuff.
when i do the gksu admin-users command i get this in the terminal and then a window pops up an say  that I'm not allowed to edit edit settings (like before)
```
hostile@hostile-desktop:~$ gksu users-admin

(users-admin:9956): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(users-admin:9956): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

(users-admin:9956): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed

(users-admin:9956): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

(users-admin:9956): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed

(users-admin:9956): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed

```

---

### Post by Kosika on 2008-02-15
So what shall i do so i can get access to the settings again?

---

### Post by Kosika on 2008-02-19
Since i got no help my solution was to Reinstall, And now i'm more carefull with editing users :)

---

