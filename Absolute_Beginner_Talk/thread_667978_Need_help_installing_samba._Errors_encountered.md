---
title: "Need help installing samba. Errors encountered"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by liaogz on 2008-01-14
Hi all,

I need help for installing samba. It is not fully installed and i do not know why. The following are the codes that I received...

root@moses:~# sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.6) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

And this is the error when i work on a testpram

root@moses:~# sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
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


Anybody can help? I need this problem to be solved in order to connect to the company's workgroup.

---

### Post by mikeyphi on 2008-01-15
Just one suggestion..... Open a terminal and enter:

sudo dpkg --configure -a

Hopefully that might resolve the installation problem.

---

### Post by liaogz on 2008-01-15
nope. it doesnt work

root@moses:/home/moses# sudo dpkg --configure -a
Setting up samba (3.0.22-1ubuntu3.6) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba

---

