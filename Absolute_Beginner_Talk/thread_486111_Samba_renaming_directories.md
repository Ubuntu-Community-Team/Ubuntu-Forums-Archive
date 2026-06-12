---
title: "Samba renaming directories??"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2007-06-27
Does samba rename directories if they are over a certain length? i am moving stuff from a Mac to my samba share on a raid and it seems to rename the directory on me...

---

### Post by PCFascist on 2007-06-27
What is the file system you are moving to?
I would guess it is making them shorter because the samba knows the file system can't support the long file names... but that is my only guess.

---

### Post by huggy77 on 2007-07-02
System Settings say that it is ext3...  

smb.conf
```

####### GLOBAL #######
[global]
workgroup = aerialphotos
server string = Skunkworks 
;   wins support = no
;   wins server = w.x.y.z
dns proxy = no
;   name resolve order = lmhosts host wins bcast
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true
load printers = no
log file = /var/log/samba/log.%m
max log size = 1000
;   syslog only = no
syslog = 0
panic action = /usr/share/samba/panic-action %d

####### Authentication #######
security = user
encrypt passwords = true
passdb backend = smbpasswd
obey pam restrictions = no
;   guest account = nobody
invalid users = root
;   unix password sync = no
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
;   pam password change = no

########## Domains ###########
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

############ Misc ############
;   include = /home/samba/etc/smb.conf.%m
socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

############ SHARES ############
[RAID]
comment=raid - BACKUP ONLY
path=/mnt/raid
validusers=clegge, JMajoris, CCompton
public=yes
writeable=yes
browseable=Yes
createmask=0777

[CLEGGE]
comment=raid - BACKUP ONLY
path=/data/clegge
validusers=clegge
public=yes
writeable=yes
browseable=Yes

[SRC]
comment=raid - BACKUP ONLY
path=/usr/src
validusers=clegge
public=yes
writeable=yes
browseable=Yes

[skunkShare]
comment=General Office Share
path=/data/skunkShare
valid users=clegge, JMajoris, CCompton, STravellin
public=yes
writeable=yes
browseable=Yes

[skunkWWW]
comment=www
path=/data/www/sites/
validusers=clegge
public=yes
writeable=yes
browseable=Yes


[PhotosStorage]
comment= all our photos go here...
path=/mnt/raid/RaidPhotosStorage
public=yes
writeable=yes
browseable=Yes




```


thank your for trying to help me sort this one out...  i am going to peak at my samba log files

---

### Post by huggy77 on 2007-07-02
smb logs look clean - is there anyplace else to check?

---

### Post by huggy77 on 2007-07-02
ran TESTPARM and got the following message...
```
root@skunkworks:/etc/samba# testparm smb.conf
Load smb config files from smb.conf
Processing section "[RAID]"
Processing section "[CLEGGE]"
Processing section "[SRC]"
Processing section "[skunkShare]"
Processing section "[skunkWWW]"
Processing section "[PhotosStorage]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
```

so i shortened down the offender (PhotosStorage) the share i was having the issues on and away we go....

---

