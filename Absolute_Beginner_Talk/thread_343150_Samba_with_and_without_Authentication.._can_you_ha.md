---
title: "Samba with and without Authentication.. can you have both?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2007-01-21
Hi All,

I have been using 6.06 Dapper for about 6 months, and it's great as my web/ftp/samba server.

It's been ages since I setup the samba part of it, but I can have all Windows users on the workgroup access the samba pubic share with no authentication.

Has proved a godsend.  People can access all their files, and all the Windows PCs backup at night to the server.  Great stuff.

However, I want to know if I can keep the public non authentication share and create a home/group/public share (not sure of the differences) that requires authentication (user name and password).  Preferably the same username and password as my Ubuntu login....

Any advice would be great.

I looked at the Ubuntu dapper guide (which is a great n00bie guide in itself), but I'm getting the impression that I can't have both as when editing the smb.conf file, for authentication I have it as 

```
security = user
with the username mapping
```

and for no samba authentication

```
security = share
```

Please tell me I'm wrong #-o

---

### Post by poningru on 2007-01-21
> **DarkKoopa said:**
> Hi All,

I have been using 6.06 Dapper for about 6 months, and it's great as my web/ftp/samba server.

It's been ages since I setup the samba part of it, but I can have all Windows users on the workgroup access the samba pubic share with no authentication.

Has proved a godsend.  People can access all their files, and all the Windows PCs backup at night to the server.  Great stuff.

However, I want to know if I can keep the public non authentication share and create a home/group/public share (not sure of the differences) that requires authentication (user name and password).  Preferably the same username and password as my Ubuntu login....

Any advice would be great.

I looked at the Ubuntu dapper guide (which is a great n00bie guide in itself), but I'm getting the impression that I can't have both as when editing the smb.conf file, for authentication I have it as 

```
security = user
with the username mapping
```

and for no samba authentication

```
security = share
```

Please tell me I'm wrong #-o

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
that will tell you how to use your linux user stuff.
but I would recommend using the windows domain stuff [https://help.ubuntu.com/community/SettingUpSambaPDC](https://help.ubuntu.com/community/SettingUpSambaPDC)

---

### Post by DarkKoopa on 2007-01-22
> **poningru said:**
> [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
that will tell you how to use your linux user stuff.
but I would recommend using the windows domain stuff [https://help.ubuntu.com/community/SettingUpSambaPDC](https://help.ubuntu.com/community/SettingUpSambaPDC)


Thanks for the guide.

I have played around with the smb.conf a bit, and at the moment I can access the first share (by mapping it in Windows and the using the different login window) with the PCs and it works great.

The second share, the one I want to be secured, I'm having issues with.

I have tried using the valid users command but when I enter in my username and password, it just re-prompts me for it.

I have created a second user for the common share, and used the smbpasswd command to set passwords for it.  (I use the test parm command and restasrt the service every time I have made a change.....)

I have also done this for the main account in Ubuntu which I want to access the secured share, but it won't work.

```
[global]
        workgroup = MSHOME
        server string = Ubuntu Samba
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
        hosts allow = 127.0.0.1, 192.168.1.
        hosts deny = ALL

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Public]
        comment = Backup and Storage Share
        path = /mnt/backup_drive
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

[[B]Secured]
        comment = Secured data drive
        path = /home/secured
        valid users = darkkoopa
        force user = darkkoopa
        read only = No
        create mask = 0777
        directory mask = 0777
        browseable = No[/B]
```

Please help!  It's driving me nuts.....

---

### Post by maikoherajin on 2007-02-03
> **DarkKoopa said:**
> 
The second share, the one I want to be secured, I'm having issues with.


I have gotten a simliar setup to work, with one semi-serious caveat. If the first share a user accesses on the host computer after they login to Windows is the secured share, they enter their password, and then can access that share, and the public one as well. If, however, the user accesses the public share first, and then tries to access the private share, it prompts for the password, but then informs them that they can not access it, because multiple connections using diferent login names are not allowed. I assume this means that accessing the public share first causes them to be logged on as "nobody" or maybe "guest". I'm not sure if this behavior is by design, but it sure is annoying. Anyway, the workaround is to permenantly map one of the secured shares to a windows drive. Either that, or make sure the user understands they have to access the secured directory first. (:

Anyway, here's the relevant config code to how I did it. (modified via the KDE gui config, if that makes any difference) If anyone else has a better solution, I'm all ears.

```

[global]
security = user
map to guest = Bad User
restrict anonymous = no
guest ok = yes
domain master = no
preferred master = no
netbios name = Ferret Tunnel
workgroup = TS!
server string = Stand by to ferret! Wow!
max protocol = NT
ldap ssl = No
server signing = Auto

#The public directory - duh.
[Public]
case sensitive = no
msdfs proxy = no
read only = no
path = /home/public/

#The secured directory - note that maikoherajin has both read and write access. I assume that is not nessisary depending on your purposes. It is for mine. (:

[Download]
valid users = maikoherajin
write list = maikoherajin
case sensitive = no
msdfs proxy = no
read only = no
path = /home/maikoherajin/download/

```

---

