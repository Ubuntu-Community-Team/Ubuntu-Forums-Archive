---
title: "Samba &quot;Testparm&quot; error"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-05-25
I'm getting this error:

> sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


This is a fresh install of Dapper, and Samba, I haven't even edited the file yet.

---

### Post by christhemonkey on 2007-05-25
What error?
This one?:
> WARNING: passdb expand explicit = yes is deprecated
I think this is just a compiled in default that you can explicitly disable, i've never had a problem leaving it on though.

---

### Post by homerj742 on 2007-05-25
Yes, that's the one. 

I'll leave it then and see how things work out, thank you!

---

### Post by waqas_butt0071 on 2007-07-25
well on my system it is working fine but i do ot know what it is for i have installed the samba server and configured its config file. but i do not know what this command does.

---

