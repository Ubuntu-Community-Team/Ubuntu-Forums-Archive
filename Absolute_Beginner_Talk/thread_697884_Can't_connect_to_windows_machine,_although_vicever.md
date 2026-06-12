---
title: "Can't connect to windows machine, although viceversa is possible"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by artod on 2008-02-15
Hello,
I have a problem with my network: I have a network with two computers, a Windows XP Professional one and another one on which I just installed Ubuntu Gutsy.
I have set up Samba and I manage to connect to the Linux machine from Windows, but can't do it the other way around: I see the workgroup, but I can't list the computers in the group.
When I try to connect to the Windows machine from command line, smbclient works just fine with smbclient //hostname.workgroup/sharename .

What am I doing wrong?

My smb.conf is as follows:

[global]

workgroup = WORKGROUP
netbios name = PCONE

server string = %h

encrypt passwords = yes
hosts allow = 192.

dns proxy = no

log file = /var/log/samba/log.%m

max log size = 1000

syslog = 0

panic action = /usr/share/samba/panic-action %d

   security = user

encrypt passwords = yes

passdb backend = tdbsam

obey pam restrictions = yes

invalid users = root

passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

   domain logons = yes
   logon path = \\%N\profiles\%U

   load printers = yes

socket options = TCP_NODELAY 

wins support = no
[homes]
   comment = Home Directories
   read only = no
   browseable = yes
   write list user1, user2

   writable = yes

   create mask = 0775
   directory mask = 0775

wins support = no
restrict anonymous = no
domain master = yes
preferred master = yes
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto

[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
create mask = 0700

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[share1-name]
path = /home/user1
guest ok = no
valid users = user1 user2 user3 user4
read only = no
available = yes
browsable = yes
public = yes
writable = yes

The network has static IPs and no servers.

---

### Post by Discov3ry on 2008-02-15
Did you disable the XP firewall?

---

### Post by artod on 2008-02-16
Yes, I did disable the windows firewall and ZoneAlarm.

---

