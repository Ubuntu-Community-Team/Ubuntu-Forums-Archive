---
title: "persistent samba print settings"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-11-15
hello,

i have a printer on my desktop machine (dapper) and i'm trying to print from my laptop (edgy).

it works, but only if i renew the printer settings on the laptop after every reboot.  i have to enter the network address, username and password every time.

what gives; is it the laptop or the samba config file?

let me know what additional info i should post; thanks!
-steve

---

### Post by BarfBag on 2006-11-15
I don't think I can contribute any advise on getting it working, but I'll give you a bump and a piece of advise so that others can help you fix it faster.  Post your Samba config file.

---

### Post by stevieb on 2006-11-15
thanks, here it is, with most of the commented lines removed:

first, though- a stupid question:  do i need to have samba set up on the laptop as well?  thanks!

```
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

   workgroup = MSHOME


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

;   security = user

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

;   unix password sync = no

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

;   pam password change = no

########## Domains ###########

;   domain logons = yes
#
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

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no

;   valid users = %S

;   writable = no

;   create mask = 0600

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

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
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

#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

---

