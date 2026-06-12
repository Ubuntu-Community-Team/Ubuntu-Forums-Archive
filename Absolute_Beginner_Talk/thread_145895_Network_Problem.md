---
title: "Network Problem"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Kenas on 2006-03-17
Hi,
I am getting network problems with other windows users.
I can Ping all the computers in my network but i can not access to the WorkGroup.
I have SMB installed already.

I am complete noob so pls can someone explain me step by step all the procedure i should follow ?

---

### Post by Iowan on 2006-03-17
What workgroup is Samba set to serve?  Unfortunately, I'm away from my Samba box, so I can't look up the smb.conf file to see what else may be issues.

Do you have accounts set up for the users.

---

### Post by dermotti on 2006-03-17
System --> Shared Folder --> Add --> General Windows Sharing Settings

change domain /workgroup to workgroup

Thats how i did it anyways ,worked after reboot.

otherwise

sudo vi /etc/samba/smb.conf

change the line 27 to **workgroup = workgroup**

---

### Post by Kenas on 2006-03-17
My workgroup is correctly configured.

---

