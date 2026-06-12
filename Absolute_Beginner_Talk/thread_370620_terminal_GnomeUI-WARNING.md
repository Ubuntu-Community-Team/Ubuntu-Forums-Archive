---
title: "terminal GnomeUI-WARNING"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by klein de usa on 2007-02-25
hi
has anyone ever seen this before ? i just noticed it, and now i have a pop up window for my password and not the prompt in terminal?

klein@klein:~$ gksudo gedit /etc/modprobe.d/aliases
(gedit:5172): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
klein@klein:~$ gksudo gedit /etc/hosts

(gedit:5235): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
klein@klein:~$

---

### Post by dcstar on 2007-02-25
> **klein de usa said:**
> hi
has anyone ever seen this before ? i just noticed it, and now i have a pop up window for my password and not the prompt in terminal?

klein@klein:~$ gksudo gedit /etc/modprobe.d/aliases
(gedit:5172): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
klein@klein:~$ gksudo gedit /etc/hosts

(gedit:5235): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
klein@klein:~$

Ignore, they are just normal artifacts from running X commands in a terminal window.

---

### Post by aysiu on 2007-02-25
That's a bug, not a real error. Just go with it.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

