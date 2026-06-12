---
title: "Double Samba Shares"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2007-01-01
A minor oddity:  I set up samba sharing by editing smb.conf.  I uncommented the lines:
```
[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
```
Went to my windows machine, entered my username & password, and I get two directory shares from the samba server--"<username>" and "homes".  They have identical content--my home directory.  Anybody know why?

Thanks,
Buck

---

### Post by kidders on 2007-01-01
Hi there,

Could you post the rest of your smb.conf ... just in case.

---

### Post by Buck2348 on 2007-01-01
> **kidders said:**
> Could you post the rest of your smb.conf ... just in case.
Glad to:
  >  workgroup = MSHOME
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
[homes]
   comment = Home Directories
   browseable = no
   writable = yes
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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
I hope I deleted only the comments.  I believe it's all default except for the four [homes] lines.  Thanks for your reply.

Buck

---

### Post by kidders on 2007-01-01
Curious. :-k "browseable=no" usually hides the "homes" share. What happens if you add "valid users = %S" or "guest ok = no" to the [homes] section?

---

### Post by Buck2348 on 2007-01-01
After 3 or 4 reboots and one more restart of samba the problem is fixed.  Thanks very much for your replies.  Sorry to bother about something so trivial.

Buck

---

