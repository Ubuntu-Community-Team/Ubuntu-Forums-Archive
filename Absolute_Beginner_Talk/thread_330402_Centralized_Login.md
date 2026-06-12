---
title: "Centralized Login?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-01-03
Hello

I want a centralized login for all of my networked Ubuntu computers. I have plenty of extra spare computers to use as a server for this purpose.

Does anyone know how I would accomplish this?

---

### Post by sardion on 2007-01-03
The easiest thing to do would be to make /etc and /home mount from the network drive.  Mounting /etc from the network drive may be a little tricky since you can't just put an entry in fstab.  Perhaps someone else knows how to do that?  Alternately, just mount /home from the network and make sure the /etc/passwd and such are mirrored correctly (perhaps with a cron job)?

You could also just do a network boot and not install anything on the client machines.

---

### Post by jondecker76 on 2007-01-03
Hmm..  I'm just learning Linux so mounting the /etc and /home is a bit beyone my scope anyways.

How would I net boot? Is there some sort of PXE server?

thanks

---

### Post by Olav on 2007-01-03
> **jondecker76 said:**
> How would I net boot? Is there some sort of PXE server?

There is, you might want to take a look at the [Linux Terminal Server Project]("http://www.ltsp.org/").

To have "centralized login" as you call it, you certainly do not need all this or to mount any /etc partitions. Just install [NIS]("http://packages.ubuntu.com/edgy/net/nis") and learn how to use it. Sorry can't help you much, it has been years since I have done this but I remember it was easy.

Mounting home directories from a server is slick though, you could logon to any machine and still have the same environment.

---

### Post by bluefrog on 2007-01-03
you may install edubuntu to go the easy way. the server will centralize the logins and the thin client will use it. In that configuration only the server needs to be full of RAM.

But as I understand that you have already plenty of configured computers, the best thing would be to install an LDAP server and authtenticate against it.

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

James

---

