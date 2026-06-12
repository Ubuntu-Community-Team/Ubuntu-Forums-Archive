---
title: "Samba shares - no acces"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by IamAcoconut on 2007-01-03
Hi! 
Nobody answered this question, maybe it's so obvious, that it should belong here...

The problem is that I can't acces shares on my local Samba server.
- The connection's ok - the server is at the same time a gateway for computers in my home network.
- The server's running on SuSE linux.
- I could acces the files when running SuSE on my PC, but now that I switched to Ubuntu I can only see that there's "Windows Network", not even the name of the workgroup is displayed.

Thanks in advance :)

---

### Post by Spinelli on 2007-01-03
We need a little bit more information about the situation. 

1. What version of Suse are you using?
2. What version of Samba are you using?
3. What version of Ubuntu are you using?
4. What client program are you using to access the file server?
5. What does your /etc/samba/smb.conf file look like?

---

### Post by tagra123 on 2007-01-03
> **Spinelli said:**
> We need a little bit more information about the situation. 

1. What version of Suse are you using?
2. What version of Samba are you using?
3. What version of Ubuntu are you using?
4. What client program are you using to access the file server?
5. What does your /etc/samba/smb.conf file look like?

Hi!
Nobody answered this question, maybe it's so obvious, that it should belong here...

The problem is that I can't acces shares on my local Samba server.
- The connection's ok - the server is at the same time a gateway for computers in my home network.
- The server's running on SuSE linux.
- I could acces the files when running SuSE on my PC, but now that I switched to Ubuntu I can only see that there's "Windows Network", not even the name of the workgroup is displayed.

Thanks in advance 





Try this it took me six months, but I finally got it to work on my boxes. My problem was exactly what you are experiencing.

Mainly the problem seemed to be nautilus couldn't see the share -- windows could see but not access the share.

Anyway this should help you.

[http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18)

---

### Post by IamAcoconut on 2007-01-03
> **Spinelli said:**
> We need a little bit more information about the situation. 

1. What version of Suse are you using?
2. What version of Samba are you using?
3. What version of Ubuntu are you using?
4. What client program are you using to access the file server?
5. What does your /etc/samba/smb.conf file look like?
Thanks for quick response!

1. SuSE 10.1
2. Samba 3.0.22-11
3. Ubuntu 6.06 LTS
4. Nautilus
5.```
[global]
        workgroup = HOME
        interfaces = eth0, eth2
        security = DOMAIN
        map to guest = Bad User
        printcap name = cups
        logon path = \\%L\profiles\.msprofile
        logon drive = P:
        logon home = \\%L\%U\.9xprofile
        usershare max shares = 100
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        cups options = raw
        include = /etc/samba/dhcp.conf

[printers]
        comment = All Printers
        path = /var/tmp
        create mask = 0600
        printable = Yes
        browseable = No

[shared]
        comment = shared
        path = /home/nec/shared
        force user = nec
        read only = No
        guest ok = Yes
```

Thanks, **tagra123**, I'll try that!

---

### Post by IamAcoconut on 2007-01-11
I tried it, tagra. To no avail.
I'm still stuck.

---

### Post by tagra123 on 2007-01-12
Try installing Firestarter ( universe repo )

sudo apt-get install firestarter


Start firestarter and enable port 139 and se if that helps.

By default iptables (a firewall is protecting your system) Firestarter is an easy way to give access to ports and machines.  You can temporarly disable the firewall completly by clicking stop -- using firestarter.  See if you can get the connection to work trying this.

Did you, by chance add the ubuntu username to samba on the suse machine?

---

