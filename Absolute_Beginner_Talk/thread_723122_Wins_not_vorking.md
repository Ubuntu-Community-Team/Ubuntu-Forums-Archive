---
title: "Wins not vorking"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by ruda on 2008-03-13
Hello everyone
I'm running about 40 computers on my network. Recently I installed ubuntu and wanted to configure wins for my work group in samba. After this i will also try to configure a domain controller on it. other computers on my network are xp pro, home and win 2000 platforms. so I configured samba, probably not correct because there is no computers to browse in my work group. not on ubuntu machine, not on any other pc in network. recently I find out that win 2000 on my network beat the **** out of me in master browser election so I stopped browser service on that machine, but still nothing. here is my smb.conf:
global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = EUROM

# server string is the equivalent of the NT Description field
   server string = domain controller
   netbios name = ed
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = yes

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = wins bcast host 
   local master = yes
   os level = 99


#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = lo eth1

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = true
Any suggestions??

---

### Post by ruda on 2008-03-13
also I would be grateful if someone can explain what are those host aliases in network settings. First two have address 127.0.0.1, should I change that to my local IP or what??

Thnx

---

### Post by ruda on 2008-03-13
This is my smb.conf file without comment lines.
I just find out i can get it wit testparm command 
[global]
        workgroup = EUROM
        server string = domain controller
        interfaces = domain.eurom
        bind interfaces only = Yes
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = wins bcast host
        os level = 99
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

---

