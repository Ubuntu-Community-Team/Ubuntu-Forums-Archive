---
title: "can see Ubuntu server but cant gain access from Windows"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by turbobill on 2007-11-12
Hello,

Installed Ubuntu 7.10 Server, then installed desktop.  Answered yes to Samba during install.

have set up shared directories on server including one totally open to the world with all permissions for everyone.

from windows i can see it but the logon just won't let me in.  Do I need to load Samba on Windows, too?

Please help.
Wm

P.S. I have searched through the earlier posts with no definite answers.

---

### Post by maybeway36 on 2007-11-12
Is the security level set to user? What version of Windows is it?

---

### Post by turbobill on 2007-11-12
Is the security level set to user? = NO
Windows version = XP sp2

So is it safe to assume that we don't need Samba installed on Windows?

Thanks,
Wm

---

### Post by turbobill on 2007-11-12
Where do you set the security level to user?

---

### Post by jessika-kaos on 2007-11-15
I'm having a similar issue. I have a directory I want to share with no security or logon, and can see it from the windows PC but I can't access it. I had this working before, but I reinstalled gutsy and now I can't seem to make it work. 

Here's the uncommented sections of my samba.conf. Maybe I just am missing something?

```
[global]

   workgroup = MIND
   server string = %h server (Samba, Ubuntu)
   dns proxy = no


#Authentication

   security = share
   passdb backend = tdbsam
   obey pam restrictions = yes
   guest account = nobody
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .


#Misc

   socket options = TCP_NODELAY


#Share Definitions


[public]
  comment = Public Folder
  path = /dev/hda1
  guest ok = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

[public]
  comment = Public Folder
  path = /dev/sda3
  guest ok = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup



```

---

