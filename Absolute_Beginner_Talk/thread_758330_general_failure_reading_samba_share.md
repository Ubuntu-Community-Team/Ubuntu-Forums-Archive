---
title: "general failure reading samba share"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by djules26 on 2008-04-17
Tried to copy my DOS based program on my ubuntu samba shared folder(/windows/share) acting as server. My client computer is running windows 98 OS, tried to access and run my DOS based program from that samba shared folder from WINDOWS 98 and got this error GENERAL FAILURE READING DRIVE Z:(my MAP drive) ABORT, RETRY, FAIL?   my question is WHY have this error?

if i do the same process under windows xp it has no problem at all. i can run my DOS based program with no error.

that samba shared folder is accessible to everyone(RW permission enabled).

Can somebody please explain? thanks

---

### Post by DBrocks on 2008-04-19
Most likely a driver issue with 98. It should work though. Could you post the contents of your /etc/samba/smb.conf? (Blur out sensitive stuff though :lolflag:)

---

### Post by djules26 on 2008-04-20
thanks for the reply...this is my smb.conf

#======================= Global Settings =======================

[global]
   workgroup = Workgroup
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = share
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
;   pam password change = no

########## Domains ###########
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########
;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @lpadmin

############ Misc ############
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directory
browseable = yes
;   valid users = %S
   writable = yes
;   create mask = 0700
;   directory mask = 0700

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[Home]
path = /home/rbdi-ipil/pcbr2   --------> this is where my DOS program resides(pc.bat)
available = yes
browsable = yes
public = yes
writable = yes

---

