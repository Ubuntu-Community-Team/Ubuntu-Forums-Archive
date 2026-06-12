---
title: "Samba Problems once more."
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by serfczar on 2007-08-15
Once this machine is viewable under windows, I can't see any of the other machines on my network, what did I do wrong?

---

### Post by serfczar on 2007-08-16
bump.

---

### Post by HereInOz on 2007-08-16
If you told us what you did actually do, we may be able to assist in what you did wrong.

Samba with Ubuntu is very easy, and if you get it right, it just works, so give us an outline of how you went about it and what you did, and someone may be able to pick up on the error.

Are you telling us that you are able to see the samba share from a windows machine, but all the other machines on the network are now invisible?

---

### Post by serfczar on 2007-08-16
> **HereInOz said:**
> If you told us what you did actually do, we may be able to assist in what you did wrong.

Samba with Ubuntu is very easy, and if you get it right, it just works, so give us an outline of how you went about it and what you did, and someone may be able to pick up on the error.

Are you telling us that you are able to see the samba share from a windows machine, but all the other machines on the network are now invisible?

That's what i'm telling you, I thought this may be a simple mistake that was well known and I didn't need to include my config. 

Here it is.

workgroup = WORKGROUP

server string - %h server (Samba, Ubuntu)

dns proxy = no

log file = /var/log/samba/log.%m

max log size = 1000

syslog = 0

panic action = /usr/share/samba/panic action %d

encrypt passwords = true

passdb backend = tdbsam

obey pam restrictions = yes

invalid users = root

passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword: * %n\n *Retype\snew\sUNIX\spassword:*%n\n *password\supdated\ssucessfully* .

socket option = TCP_NODELAY

[printers]

comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
public = no
writable = no
create mode = 0700

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no

[Iso Server]
writeable = yes
valid users = serfczar
user = serfczar
path = /iso
write list = serfczar

---

