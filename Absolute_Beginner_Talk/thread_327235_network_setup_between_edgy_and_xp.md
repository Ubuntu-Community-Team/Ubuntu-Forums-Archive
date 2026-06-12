---
title: "network setup between edgy and xp"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-12-28
is it possible to set up a network between an edgy box and an xp box i have some files i would like to transfer to the xp box how could i do this?

---

### Post by punx45 on 2006-12-28
there are a couple options:

for an occasional file transfer you could install openSSH on the ubuntu machine and use an SFTP client like winSCP on the windows machine..

or more more frequent use i would install SAMBA on the ubuntu machine and use Windows sharing to share folders between the two computers.

---

### Post by nhandler on 2006-12-28
I would also recommend using samba. It took me maybe 5 minutes to set up. After that, it worked perfectly. It needed to configuration or programs on the windows box at all. The ubuntu guide ([http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)) has some nice info on how to go about using Samba. Also, the ubuntu wiki ([http://wiki.ubuntu.com](http://wiki.ubuntu.com)) has some information as well.

---

