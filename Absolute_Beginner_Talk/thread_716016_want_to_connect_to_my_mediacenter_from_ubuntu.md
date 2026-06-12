---
title: "want to connect to my mediacenter from ubuntu?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by brum8 on 2008-03-05
Hey 

i wonder if there is such a thing as connection from ubuntu to windows mediacenter
as like radmin or vnc viewer,

and if not or know the solution to how i can connect to my home network MSHOME with computer name MEDIACENTER and shared map DOWNLOAD?? :)

---

### Post by neurostu on 2008-03-05
What exactly is it you want to do? Just to connect and share files? or to remotely use the desktop?

---

### Post by brum8 on 2008-03-05
hehe to clarify

1. remote
2, share

my keyboard is knackered to my mediacenter rofl

---

### Post by neurostu on 2008-03-05
When you say "remote" what exactly do you mean by that?

when you say share i assume you mean share files across the network? right?

---

### Post by newlinux on 2008-03-05
For remote control of your desktop, depending on what you want to do, you can look into installing a vncserver on your windows machine and using VNC, or using terminal server client (like remote desktop).

For file sharing you can look into using SAMBA/CIFS.

---

### Post by brum8 on 2008-03-05
Well as u said remotely use the windows mediacenter desktop got my computer fooked up from this linux so i cant install xp again so i got an radmin server on mediacenter :)

---

### Post by brum8 on 2008-03-05
I think i got all the files for samba but how do i open it :S

---

### Post by newlinux on 2008-03-05
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Is a good guide for SAMBA. CIFS is the more up to date standard, but SAMBA will work fine. You can easily switch to using CIFS.

---

