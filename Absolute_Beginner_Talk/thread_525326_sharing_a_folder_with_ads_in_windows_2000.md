---
title: "sharing a folder with ads in windows 2000"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by puneetbrar on 2007-08-14
i am newbie with linux 

i have a problem i am using ubuntu 7.04 and the system is working perfectly infact it joined the windows domain also but my problem is that i am unable to share folders to windows i have configured samba in smb.conf 

i have joined a domain and klist and kinit and wbinfo all works fine but when i share a folder i am unable to browse it from the windows it says network access denied 
can anybody help


[global]

security = ads
security = user
username map = /etc/samba/smbusers
name resolve order = host wins bcast
enable privileges =Yes
allow trusted domains = No
#netbios name = linux
printcap name = cups
printing = cups
cups options = raw
realm = FCSINDIA.COM
password server = 192.168.2.2
;workgroup = FCSINDIA
idmap uid = 16777217-33554431
idmap gid = 16777217-33554431
#winbind separator = +
winbind enum users = yes
winbind enum groups = yes 
winbind use default domain = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
client ntlmv2 auth = yes
encrypt passwords = yes
winbind use default domain = yes
restrict anonymous = 10
server string = %h server (Samba %v, Ubuntu)
writable = yes
browseable=yes 

# to avoid the workstation from
# trying to become a master browser
# on your windows network add the
# following lines
domain master = no
local master = no
preferred master = no
os level = 0


#======================= Share Definitions =======================
wins support = yes
workgroup = FCSINDIA.COM
[data]
comment = Share Data
path = /home/data
read only = No
create mask = 0775
directory mask = 0775
browsable = no
public = no

force create mode = 0775
force directory mode = 0775
force security mode = 0775
guest ok = no
inherit permissions = yes
nt acl support = yes

available = no
writable = no
[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = no
writable = no
create mode = 0700




[software data]
path = /media/hdd2
available = yes
browsable = yes
public = yes
writable = no

[hdd2]
path = /media/hdd2
available = yes
browsable = yes
public = yes
writable = yes


[sfddata]
path = /media/hdd2
available = yes
browsable = yes
public = yes
writable = no



   [ShareMe]


path = /home/shareme
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
available = yes
browsable = yes

---

### Post by grimmoner on 2007-08-15
i hope already got your shares working.

i also hope you didnt missed that,
have you got the samba daemon restarted?
so the changes in smb.conf will take effect.

sudo /etc/init.d/samba restart

---

