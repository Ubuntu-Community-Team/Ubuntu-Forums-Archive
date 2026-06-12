---
title: "Windows Networking"
date: 2008-02-07
forum: Apple PPC Users
---

### Post by imacbrett on 2008-02-07
I have just install Ubuntu 6.10 on my iMac G3 DV 400MHz system.  Every things install correctly and the system runs fine.  The only thing is that I am having a difficult time networking it with my other PC running Windows Vista Ultimate.  My PC shows up in the networking center, but I am having trouble accessing it.  Also when I use the terminal to access the "/etc /smba/smb.conf," nothing shows up in the gedit.  The page is blank.

---

### Post by Zack McCool on 2008-02-07
The config file should be at:

/etc/samba/smb.conf

Also, make sure you have installed samba, samba-common, smbclient and smbfs.  The following will make sure you have everything you need installed:

```

sudo apt-get install samba samba-common smbclient smbfs

```

Once that is done, edit your /etc/samba/smb.conf to make sure all of the settings match your LAN.

Then, you need to add a user.  sudo smbpasswd -a username

Use your normal linux username for that.  First, you'll be asked for your Ubuntu password (for sudo), then it will ask for a smb password for the new user, and a confirmation.  This doesn't have to be the same password as your linux account, but it can be if you wish.

Once it is all set up, you should be set.

---

### Post by renzokuken on 2008-02-07
have you actually got samba installed?

if not install it via synaptic, then edit smb.conf using

```
gksudo gedit /etc/samba/smb.conf
```

---

