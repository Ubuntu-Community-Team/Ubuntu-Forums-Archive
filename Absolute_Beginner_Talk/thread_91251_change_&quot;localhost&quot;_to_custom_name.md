---
title: "change &quot;localhost&quot; to custom name"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by richieboy on 2005-11-16
i'd like to change my host name to a custom name so that it reads: "richie@customname" in the command line.  how do i do this?
thanks,
rich

---

### Post by earobinson on 2005-11-16
System -> Administration -> Network settings

you need a password, then go to general and change away my friend :)

This might require a reboot

---

### Post by jdong on 2005-11-16
or, edit the contents of /etc/hostname (and /etc/hosts to make sure that it matches properly)

---

### Post by Joe_lurker on 2005-11-16
You should not change the 127.0.0.1  localhost.localdomain line in the /etc/hosts file.  This is the name of the loopback interface for the computer, not a computer name.  Some software may fail to function correctly if you change this.

-Joe

---

### Post by earobinson on 2005-11-16
[QUOTE=Joe_lurker]You should not change the 127.0.0.1  localhost.localdomain line in the /etc/hosts file.  This is the name of the loopback interface for the computer, not a computer name.  Some software may fail to function correctly if you change this.

-Joe[/QUOTE]
really, can you give me an example, I thought that thats what the gui did.

---

### Post by jdong on 2005-11-16
localhost should always be defined (because networking apps require it)... In addition, /etc/hostname should be resolvable to 127.0.0.1 because otherwise GNOME apps will fail to start.

---

### Post by earobinson on 2005-11-17
Yes i understand that. But I thought that the gui that I told the OP to use changed the same file that you told the OP to edit... no? (not on my linux box or i would check)

---

