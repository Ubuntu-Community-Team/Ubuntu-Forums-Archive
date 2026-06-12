---
title: "Xbuntu server for WinXP network, configure?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by GranPaSmurf on 2007-11-06
With all that is written about configuring Samba, I am almost reluctant to post; Please forgive my lack of Linux experience.
I am building a box to be file server & ftp to add into my WinXP network. Please tell me if an obvious error jumps out at anyone.
Samba is configured thusly:
[global]
panic action = /usr/share/samba/panic-action %d
workgroup = JoyUs
netbios name = JoyUsServerBeast
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

force user = don
force group = don

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700

When I try to add the Linux box, add network place, I can see the connection but then get  "network path not found" I also tried mapping network drive with the same result. I have enabled WINS, set router to supply static IP, added Samba user & password. If you don't see something right away, can you direct me to a REALLY SIMPLE tutorial? I have looked at several & gleaned a bit from each, but, still cannot get where I want to be.
Thank you volunteers ahead of time.
dk

---

### Post by louieb on 2007-11-06
While I'm no Samba expert. Setting it up has become a breeze since I found this thread. [HOWTO: Setup Samba peer-to-peer with Windows - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202605&highlight=server")

---

