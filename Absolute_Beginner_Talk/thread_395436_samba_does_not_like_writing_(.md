---
title: "samba does not like writing :("
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-03-28
Hi,

```
# Samba config file created using SWAT
# from 192.168.0.4 (192.168.0.4)
# Date: 2007/03/28 18:09:09

[global]
        workgroup = MSHOME
        server string = (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spa$
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d

        geust account = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Downloads]
        comment = Server downloads
        path = /home/bojo/Downloads
        valid users = anybody
        guest only = Yes
        guest ok = Yes

[Proofs4]
        path = /home/bojo/Proofs4
        write list = guest , nobody, bojo
        guest only = Yes
        read only = No
        guest ok = Yes
        writeable = Yes
```

that's my smb.conf file.

however i can get in and view downloads (only want it to be read only from windows anyway). But i want the proofs4 folder to have write access, without logins.

Currently i can get into both, without logins, but i can't write to the Proofs4 file (or the other file).

What's going on?

---

### Post by 13ojo on 2007-03-28
```
[Proofs4]
        path = /home/bojo/Proofs4
        browseable = yes
        public = yes
        read only = No
        guest ok = Yes
        writeable = Yes
```

is the updated proofs4 setting with os level = 35 in the globals added to.

then

```
sudo chmod 777 /home/bojo/Proofs4
```

and now it seems to work.

However i think this is horrible way of setting it up?

---

### Post by danbopes on 2007-03-29
> **13ojo said:**
> Hi,

```
# Samba config file created using SWAT
# from 192.168.0.4 (192.168.0.4)
# Date: 2007/03/28 18:09:09

[global]
        workgroup = MSHOME
        server string = (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spa$
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d

        geust account = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Downloads]
        comment = Server downloads
        path = /home/bojo/Downloads
        valid users = anybody
        guest only = Yes
        guest ok = Yes

[Proofs4]
        path = /home/bojo/Proofs4
        write list = guest , nobody, bojo
        guest only = Yes
        read only = No
        guest ok = Yes
        writeable = Yes
```

that's my smb.conf file.

however i can get in and view downloads (only want it to be read only from windows anyway). But i want the proofs4 folder to have write access, without logins.

Currently i can get into both, without logins, but i can't write to the Proofs4 file (or the other file).

What's going on?
I also notices you spelt guest "geust"

---

