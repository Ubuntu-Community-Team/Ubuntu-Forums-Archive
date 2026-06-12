---
title: "Simple file sharing won't work!"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-06-05
I followed this right here: [http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

My windows PC can see the Ubuntu PC, in "My network places".

But, when I click on it, it asks for user/pass, and no matter what it's not taking. pls assist!

---

### Post by Ek0nomik on 2007-06-05
This isn't the exact solution you are looking for,

but you can share files using SSH.

```
sudo aptitude install openssh-server
```

Then you can install WinSCP in Windows and connect to your Ubuntu box.

---

### Post by Gina on 2007-06-05
Have you set the permissions for the directories you want to share to allow reading, writing and executing by all?  Took me a little while to work this out.  Oh, and I presume you're using **samba**

---

### Post by lazyart on 2007-06-05
lazyart's guide to simple Lin-Win file sharing

1- right click on the folder you wish to share.  Enable sharing as Samba/SMB
2- type```
sudo smbpasswd -a *username*
sudo smbpasswd -e *username*
```
3- from Windows browse to the ubuntu computer.  When prompted for password, use the ubuntu *username* and password.

Your ubuntu user will now have the same rights to the folder across the network as if they were logged onto ubuntu.

---

### Post by Nythain on 2007-06-05
make sure you set security = share instead of user

also make sure you have restarted the samba server after editing the smb.conf
sudo /etc/init.d/samba restart

other than those tips, id have to see your smb.conf
here's what mine looks like, its been stripped down, the default is way to much overkill and i couldnt get it working right so i had to start from scarp with a little help from this community
```

[global]
workgroup = WORKGROUP
security = share

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
security = share
restrict anonymous = no
domain master = no
preferred master = no

[stuff]
case sensitive = no
guest ok = yes
path = /data/
read only = no

```

---

### Post by homerj742 on 2007-06-05
thanks guys, I'll try it tonight. I was hoping it was made available in the GUI :(

---

### Post by homerj742 on 2007-06-05
> **lazyart said:**
> lazyart's guide to simple Lin-Win file sharing

1- right click on the folder you wish to share.  Enable sharing as Samba/SMB
2- type```
sudo smbpasswd -a *username*
sudo smbpasswd -e *username*
```
3- from Windows browse to the ubuntu computer.  When prompted for password, use the ubuntu *username* and password.

Your ubuntu user will now have the same rights to the folder across the network as if they were logged onto ubuntu.

that did it!

---

