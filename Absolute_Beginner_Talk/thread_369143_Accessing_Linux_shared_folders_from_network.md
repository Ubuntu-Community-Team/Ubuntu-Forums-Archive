---
title: "Accessing Linux shared folders from network"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-24
I tested mounting and direct acces via the smb:// on various combinations like:

1. Linux to windows:
  gotta need a guest account enabled, can't even login to the folder with the admin of the windows XP, tried both mounting and dirct and same problem.

2. Linux to Linux:
same problem as above.

3. Windows to Linux
Windows ask for the password of the only other account available then root, but doesn't accept the correct password even if entered and keeps poping up again and again for password.

---

### Post by crispy_420 on 2007-02-24
If I remember correctly, file share users are not the same as system users. You need to look for a howto on these forums for samba. Trust me there are many, depending on what you plan on doing. But it usually comes down to editing /etc/samba/smb.conf

And there is always the ftp route.

---

### Post by hyper_ch on 2007-02-24
Here's my small samba guide... not very extensive but for basic networking it's enough:

(1) Install samba
```

sudo apt-get install samba

```

(2) Backup the original samba config
```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.org
 
```

(3) Edit your samba config
```

sudo nano /etc/samba/smb.conf

```

(4) Apply *your* custom samba config
> 
[global]
workgroup = WORKGROUP
hosts deny = 10.0.0.1  #My router's IP... don't want access from outside the lan

[exchange]
comment = Exchange
path = /home/hyper/Exchange  #change this to your according path
force user = hyper  # change this to the user you want new files to be
force group = hyper  # change this the the group you want new files to be
read only = No  # enably write access in that folder

[appz]
comment = Appz
path = /home/hyper/Appz  # This is a read only folder... change path accordingly


(4) Save and quit nano
```

ctrl-x

```
```

y

```

(5) Add new system users
Only if you want to grant access to a special user that doesn't exist yet on your system...
```

sudo useradd NEW_USERNAME

```

(6) Add the new system user to samba
```

sudo smbpasswd -a NEW_USERNAME

```

(7) Reload Samba
```

sudo /etc/init.d/samba restart

```

Pretty basic but you will grant access to samba now to users... NEW_USERNAME with the samba password that you supplied can now login :)

---

