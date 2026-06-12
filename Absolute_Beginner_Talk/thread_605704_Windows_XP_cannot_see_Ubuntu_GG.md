---
title: "Windows XP cannot see Ubuntu GG"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by baagh on 2007-11-07
Hi,

I'm completely new to Linux - installed Ubuntu GG last Thursday and have been tweaking during the few minutes my baby sleeps...

**Here's what I have:**
Desktop computer solely running Ubuntu GG.
Lexmark x1150 hooked up via USB to the desktop
Belkin wireless router hooked up to Desktop via ethernet cable
Windows XP laptop (wireless)

**Here's what I can do:**
Printing and scanning from Desktop is a-ok
Desktop and laptop can access internet ok
Desktop can see the Windows laptop and access files (upload and download)

**Here's what I want to do:**
The Windows laptop cannot see/connect to my Desktop.  I'm on the same workgroup and I've enabled the laptop login/password to access Desktop files via Samba.  I've tried to map a network drive from XP using my Desktop's IP address, yet get a Windows error (I can't remember the text of the error, yet others on the Tubes have experienced it as well).  I want to be able to have the XP laptop connect to my desktop.

Please help :)

---

### Post by zvacet on 2007-11-07
[https://help.ubuntu.com/community/ComprehensiveSambaGuide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide")

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

[https://help.ubuntu.com/community/SettingUpSambaPDC]("https://help.ubuntu.com/community/SettingUpSambaPDC")

---

### Post by baagh on 2007-11-23
thanks!  I'll try those this weekend

---

### Post by hyper_ch on 2007-11-23
Here's my basic smb.conf file

```

[global]
workgroup = WORKGROUP
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

[appz]
comment = Appz
path = /home/hyper/Appz


```

First: the IP 10.0.0.1 is my router's IP. Don't want to have the smb shared accessed from outside.

Second: my primary user is hyper and all shared folders are located with my home folder. Hence I force user and group to "hyper"

Third: you need to add systemusers to your samba user file:
```

sudo smbpasswd -a hyper

```
Without users added, you cannot connect (except if you make an open share but I prefer to have some security)

After that, restart samba and it works
```

sudo /etc/init.d/samba restart

```

---

