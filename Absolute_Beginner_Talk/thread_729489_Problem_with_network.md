---
title: "Problem with network"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by turley714 on 2008-03-19
i recently built a file server using unbuntu desktop. I installed samba, SSH, x11vnc, and some FTP server that i can't think of at the moment. Anyways whenever i want to connect to my linux server from windows i must do it by manually typing the ip of the server or mapping a folder as a network drive. I would like it to show up in my network neighborhood so it will be a little easier to use for people who plug into my network and would like to use my file server. I think the problem may be in my smb.conf file but im not too sure. I'm a linux noob. below is a copy of my samba config.


[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "WORKGROUP"
netbios name = "stephen-server"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700

[bittorrent downloads]
path = /home/shared/root
available = yes
browsable = yes
public = yes
writable = no

---

### Post by Suparious on 2008-03-19
You could try using 'swat - Samba Web Administration Tool' that should be in your pacakge manager. Otherwise, a great and simple to install remote admin tool would be[ Webmin]("http://http://prdownloads.sourceforge.net/webadmin/webmin_1.400_all.deb").

Just save that .deb file and install it manually with 'dpkg'.

```
sudo dpkg -i webmin_1.400_all.deb
```

then surf to your IP on port '10000' (like [https://192.168.1.33:10000](https://192.168.1.33:10000)), login as any ubuntu user that can use 'sudo'.

---

### Post by turley714 on 2008-03-19
Yeah i tried to install swat ... i dont know what the problem was but i couldn't get it to work but i shall try again. It seamed like it would make the config process much easier

---

### Post by handydan918 on 2008-03-19
I am by no means a samba guru, but this line
```
security = user
```

might work better as ```
security = share
```

---

