---
title: "Can't see soft links in file share"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Hasen_A on 2007-05-19
Hi, file sharing is working perfectly with the following setup:
```
[global]
        workgroup = ...
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        valid users = %S
        browseable = No

[public]
        comment = Public Folder
        path = /home/public
        valid users = user1, user2 #user1,2 are correct in my conf
        force user = nobody
        force group = nogroup
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

[Bachelorarbeit]
        comment = Bachelorarbeit
        path = /home/...
        valid users = ...
        read only = No
        create mask = 0700
        directory mask = 0700

```

However, every now and then I want to share a certain folder for while. I thought of dragging a soft link into the share "public". When I enter my PC on the network I cannot see this link/folder. When I enter the IP-address "...server/public/softlink" I get an error, saying no permission.

The softlink and the parent folders both have chmod 777.

---

### Post by Metacarpal on 2007-05-19
What OS is on the computer from which you're accessing your shared folder?  If you're trying to read a Linux symlink from a Windows box, it's possible that Windows doesn't know what to do with it.

---

### Post by Hasen_A on 2007-05-19
Same problem error message **"Access Denied"** with both Ubuntu and Windows. Under Ubuntu I can't see the soft link either.

---

### Post by Metacarpal on 2007-05-19
Just re-read your initial post - are you creating a soft link in one directory, then dragging it to the shared directory?  If so, try creating the soft link in the share in the first place.

---

### Post by Hasen_A on 2007-05-20
It doesn't really matter where I create it, in a terminal or while dragging in nautilus. Creating a hard links doesn't work at all. No clue why. The help even says that certain rights won't be given even in sudo mode. Any thoughts?

---

