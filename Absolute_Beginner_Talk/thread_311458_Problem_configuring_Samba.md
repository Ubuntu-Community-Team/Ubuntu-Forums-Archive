---
title: "Problem configuring Samba"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2006-12-02
I'm having trouble configuring SAMBA between my Ubuntu Linux PC and my Windows XP-Pro PC.  From the Linux box I can connect to Samba shares on my windows box, but I cannot connect the other way -- from the Windows box to the Linux box.  

I'm using Edgy Eft on the Linux box. 

From Windows I can successfully ping my linux box both by IP and by hostname.  I'm using static IPs on my LAN, and have set the router with proper correlation of the static IPs to their respective hostnames -- and set the MAC addresses as well. 

I enabled the file sharing on the Linux box, and assigned the proper Windows workgroup.  Nonetheless, the Linux box doesn't always show up in Microsoft Windows Network, and even if it does I can't access the shares. 

I set up an encrypted Samba password for my username, using smbpasswd.

When I try to open Samba shares on the Linux server, I get this error message:
"\\Supernova\File System is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.  The network path was not found." 

I am guessing that I've somehow misconfigured the smb.conf file, specifically in the "Authentication" section.  But I could be wrong. 

I've run testparm, and find no errors.

Anyway, here is the smb.conf file:   (I've removed all the comments so my configuration is more easily readable.)
-----------

[global]
workgroup = WORKGROUP
server string = Samba Server %v
wins support = yes
dns proxy = No
hosts allow = 127. 192.168.0.
interfaces = 192.168.0.1/24 127.0.0.1/24
bind interfaces only = true
log file = /var/log/samba/log.%m
max log size = 50
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = user
encrypt passwords = Yes
smb passwd file = /etc/samba/smbpasswd
printing = cups
printcap name = cups
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
domain master = Yes
[homes]
    comment = Home Directories
    browseable = Yes
    writable = No
[printers]
    comment = All Printers
    browseable = No
    path = /tmp
    printable = Yes
    public = No
    writable = No
    create mode = 0700
[marvin]
    path = /home/marvin
    available = yes
    browsable = yes
    public = yes
    writable = no
[File System]
    path = /
    available = yes
    browsable = yes
    public = yes
    writable = no
------------

Any suggestions/help will be appreciated.

---

### Post by sardion on 2006-12-03
I never did get samba to work properly with authentication.

But I do know that if you a

guest ok = yes

in a share's section of smb.conf then it works fine

horribly insecure, but works fine.

if you, like me, have a closed local network (like are a bunch of PCs behind a router) then you can just make the shares guest accessible and it will work.

if you need to do it for real, you might have better luck at a samba specific (not ubuntu specific) forum.

---

