---
title: "apt-get or aptitude asking for cd?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by raskull on 2007-07-23
I just finished an install of ubuntu server. I installed sshd-client ok, but when installing sshd-server the same way it's asking for my "Ubuntu-Server 7.04 _Feisty Fawn_" disc in the cdrom. Now.. this seems kind of silly to me, considering the files are obviously out there on the net, and its a server so it does not have a cdrom. How can I get around this? I'm hoping there's some configuration I need to do to aptitude to prevent it from wanting the cd.

 Any help would be appreciated, thanks.

---

### Post by Mornedhel on 2007-07-23
Isn't there a CDROM entry in /etc/apt/sources.list ? Comment it out if there is one, then apt-get update.

---

### Post by Saner on 2007-07-23
System > Administration > Software Sources

(I think thats the place to set up software sources and online servers)

---

### Post by raskull on 2007-07-23
> **Mornedhel said:**
> Isn't there a CDROM entry in /etc/apt/sources.list ? Comment it out if there is one, then apt-get update.

 Perfect. Thanks... this is my first install of ubuntu so I wasn't sure where it was. It's working fine now.

---

### Post by dfreer on 2007-07-23
> **raskull said:**
> Perfect. Thanks... this is my first install of ubuntu so I wasn't sure where it was. It's working fine now.

Yeah, sometimes it doesn't always delete the CD-ROM repository from /etc/apt/sources.list upon install, I believe this normally happens if you didn't have a network configured when you installed ubuntu, although I can't be sure if it doesn't happen for other reasons.

---

### Post by raskull on 2007-07-23
> **dfreer said:**
> Yeah, sometimes it doesn't always delete the CD-ROM repository from /etc/apt/sources.list upon install, I believe this normally happens if you didn't have a network configured when you installed ubuntu, although I can't be sure if it doesn't happen for other reasons.

 Yeah I thought that was very odd. I did have network all up and running during the install because at 85% it needed it..  Seems kind of backwards that an installer requires network, then the system leavs a cdrom as a default source of application installs. Oh well, easy fix. :P

---

