---
title: "What does this mean: &quot;shift: 96: can't shift that many&quot;?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-02-10
Here's the error message i get from running "sudo nautilus":
```
(nautilus:29585): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
shift: 96: can't shift that many
```
I get similar messages running other programs su. I'm wondering if this might be related to other problems I've had recently. thanks.

---

### Post by tbroderick on 2007-02-10
Try running gksu nautilus cause sudo should only be used for console/termainl.

---

### Post by ricardisimo on 2007-02-10
```
~$ gksu nautilus
(nautilus:30157): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:30157): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
shift: 96: can't shift that many
```
Mind you, despite the error messages, whatever I'm su-ing does in fact launch.

---

