---
title: "urgent help samba problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-01
currently there's a windows me machine on my network. when i click my network neighbour i can see my ubuntu machine. when i click go -- network i can see my win me machine to. but when i double click it , it says : the folder cannot be display. when i click double click my ubuntu box in my win me machine, it keep asking for password and says my password is wrong

---

### Post by bigken on 2007-11-01
in a terminal type 

sudo smbpasswd -e yourname 

sudo smbpasswd -a yourname

---

### Post by afeasfaerw23231233 on 2007-11-01
doesn't work

---

### Post by BennBuntu on 2007-11-01
ALthough a big no no from a security point, you can allow anyone on the network to access your share without passwords.

```

sudo gedit /etc/samba/smb.conf

```

then find under Authentication heading

> security = user
replace it with > security = share

again, means anyone on local network can access your shared folders.
Can't help on the windows side.

:)

BEnn

---

### Post by bigken on 2007-11-01
did you give it a new password ? also try rebooting the pc

---

