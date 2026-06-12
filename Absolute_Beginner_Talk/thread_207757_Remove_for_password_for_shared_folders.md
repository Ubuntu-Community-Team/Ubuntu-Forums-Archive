---
title: "Remove for password for shared folders"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by helino on 2006-07-02
Hi, when I'm trying to acess my Ubuntu folders by Network places in Windows XP, I need a password and a username. I've tried with my log in username and password from the Ubuntu PC, but it doesn't work. 

Does anyone know where I can find this password, or better, disable it?

Thanks

---

### Post by someusernoob on 2006-07-02
You installed samba for the file sharing? If so:

Open a terminal and type:
```

sudo smbpasswd -a (your username)
<then type twice your password>

```

Use those on the Windows computer to login to your shared folders.

---

### Post by helino on 2006-07-02
Is there no way to disable it?

---

### Post by Demosthenes on 2006-07-05
It sounds like this could be a permissions problem, is the folder you are trying to share on (for example) a vfat partition? If so the user nobody needs to be a member of the group plugdev. This is because samba will default to user nobody for guest access, and because dapper has vfat drives owned by group plugdev.

I had a similar problem which I solved in this way.

If you want to check whether the user nobody can access the directory just:
sudo su nobody
cd /path/to/directory

---

### Post by someusernoob on 2006-07-07
If you follow 

[http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)

this guide, and change the /home/public folder to the folder you want to share, you can acces and write to it easily in Windows without the need of a password.

---

### Post by helino on 2006-07-10
Thx for all the help, the guide from someusernoob was really easy to follow

---

