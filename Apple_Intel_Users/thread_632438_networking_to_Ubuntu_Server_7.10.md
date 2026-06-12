---
title: "networking to Ubuntu Server 7.10"
date: 2007-12-05
forum: Apple Intel Users
---

### Post by vsiege on 2007-12-05
My goal for my ubunutu machine is to serve as a file server. When I installed the server software I included SAMBA. I can see the u. machine on my network  in OSX 10.4 but when I go to connect to it - it wont let me. Do I have to create a special user or change permissions?  How do I go about using SAMBA to achieve file sharing locally (on my LAN)?


Computers Systems on my network:
1x - Ubuntu Server 7.10
with Xfce desktop, LAMP Server, OpenSSH Server, PostgreSQL Database, Print Server and SAMBA
2x - OS X 10.4

Router:
Netgear

---

### Post by cyberdork33 on 2007-12-05
Samba is windows sharing format... for sharing with OSX, NFS may be the better option.

---

### Post by vsiege on 2007-12-06
what should I be doing to get that to work then? everyone keeps sending me to this [https://help.ubuntu.com/community/ComprehensiveSambaGuide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide") thats why i keep messing around with SAMBA. At present time I can mount a ubuntu disk on my mac, but you do not have to enter a password or user name (which isnt bad but im sure its not great).

---

### Post by cyberdork33 on 2007-12-06
> **vsiege said:**
> what should I be doing to get that to work then? everyone keeps sending me to this [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide) thats why i keep messing around with SAMBA. At present time I can mount a ubuntu disk on my mac, but you do not have to enter a password or user name (which isnt bad but im sure its not great).

That guide seems to be for creating a samba server on the windows machine, and connecting to it with an ubuntu machine... You want to do the opposite.

Most Ubuntu guides will focus on the GUI tools available that you normally have on Ubuntu. [https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

The main file you need to edit to setup shares is /etc/**samba**/smb.conf under the share definitions section. There are MANY, MANY options that you can mess with to get things working. You can read the man page for samba by entering the command 'man samba'.  After configuring your shares, you can start / stop the server with the init script:
```
sudo /etc/init.d/samba start
or
sudo /etc/init.d/samba stop
```

There are a LOT of guides about setting up samba, (and they are pretty much the same for any version of linux)
[http://ubuntuforums.org/showthread.php?t=76647](http://ubuntuforums.org/showthread.php?t=76647)

---

