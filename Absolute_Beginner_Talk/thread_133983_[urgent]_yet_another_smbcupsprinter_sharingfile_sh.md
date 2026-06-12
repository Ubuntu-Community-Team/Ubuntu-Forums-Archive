---
title: "[urgent] yet another smb/cups/printer sharing/file sharing problem..."
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by robinl on 2006-02-21
OK. 2 problems. First Problem:
Previously I was able to connect to my WIndows box (10.0.0.6) and browse on the shared documents using 
```
smb://10.0.0.6
```
in Nautilius. Now, after some changes to system (both to ubuntu and windows) I can't access it, or any other computer on the network. It says
```
The folder contents could not be displayed.
Sorry, couldn't display all the contents of "Windows Network: 10.0.0.6".
```
When I try to go to Places/Network Servers, it tells me "You must log in to access UBUNTU (my pc)" and my username+password doesn't work. If I cancel that no computer is displayed. I can ping the XP box normally.


Second Problem [solved]:
I'm trying to share a printer connected to Ubuntu box to the Windows box (has Windows Drivers). I've searched the forum and most are other way around and the few helpful tips are to use CUPS instead of Samba etc. [[However I couldn't get CUPS web interface to work (uncommented port 631, plus some other change. PS  is it like a mini-apache? config file look like it...). Every time i try 127.0.0.1:631 on my computer or 10.0.0.3:631 on windows firefox just say connection failed. I remember I got it working before but now it simply don't work.]] (solved)  Also, should I follow this approach instead of smb (which I still don't understand)

Sorry for the long post, and any help is appreciated.

---

### Post by slazh on 2006-02-21
What did you change? The samba config file?
Maybe you could post your samba config here, aswell as your shared documents setup on your XP box.

---

### Post by robinl on 2006-02-23
This is my smb.conf

```

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
;   security = user
   encrypt passwords = true 
   passdb backend = tdbsam guest
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
;   pam password change = no
   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
   printing = cups
   printcap name = cups
;   printer admin = @ntadmin
;   preserve case = yes
;   short preserve case = yes
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

[homes]
   comment = Home Directories
   browseable = no
   writable = no
   create mask = 0700
   directory mask = 0700
Logons
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


```

The shared documnet on Windows is just a normal everyone readable shared folder.
Thanks.

---

### Post by Yfrwlf on 2007-10-21
The default install of Feisty and also of Gutsy should allow you to see the Windows network stuff without issue.  Here is a fresh smb.conf file for you.  Be sure to change the user name of the Public share for /home/username/Public.

Hope that helps.  I don't know enough about Samba yet to help you further aside from showing you what worked for me.  If you still have issues, perhaps it's a firewall or some other problem.

---

### Post by robinl on 2007-10-21
Please don't resurrect threads that are more than 1 year old.

---

### Post by Yfrwlf on 2007-10-23
> **robinl said:**
> Please don't resurrect threads that are more than 1 year old.

Then it's too bad it can't be marked as solved or something, so no one else will try to help you with this.  How was I supposed to know if you didn't say so?  I take it you don't have this problem anymore.  Good. :)

---

### Post by robinl on 2007-10-24
Well the problem isn't really solved and I've completely forgotten about it until it showed up on my inbox. It had been 2 releases from edgy now and I've converted my other computer to Ubuntu, so I can't test the problem anymore. Thanks for helping with my problem, unfortunately you're just a year too late :)

---

