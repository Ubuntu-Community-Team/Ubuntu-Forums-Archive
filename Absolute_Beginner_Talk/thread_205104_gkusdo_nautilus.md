---
title: "gkusdo nautilus ?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-27
I type that in a terminal and it grants me root privileges,but what's this all about? Mind you, I do have root privileges !  Thanks

drakkor@drakkor:~$ gksudo nautilus
(nautilus:5570): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:5610): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
drakkor@drakkor:~$

---

### Post by aysiu on 2006-06-28
From [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) ... > **But gksudo sometimes gives me an error... even though it appears to work...**
You may notice that even though gksudo is the proper way to launch graphical applications, if you launch a gksudo application it will sometimes give you what appears to be an error. This, for example:```

(gedit:####): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

That is not a real error, and [there's already been a bug report filed on the message appearing.](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917) The developers have seen the bug and labeled it a low priority. In the meantime, just ignore the message and keep encouraging people to not use sudo for graphical applications so they won't potentially mess up their ~/.ICEauthority and other user configuration files. 

---

### Post by Drakkor on 2006-06-28
Thank as always, aysiu !  :)

---

