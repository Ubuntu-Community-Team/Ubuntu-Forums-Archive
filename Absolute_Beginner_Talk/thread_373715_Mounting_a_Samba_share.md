---
title: "Mounting a Samba share"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by tyke on 2007-03-01
Hi, I was wondering if anyone could help me with this.

I'm trying to mount a Samba share with read/write access. my fstab entry looks like this:
```

//study-desk/MyFiles	/home/tyke/server	smbfs username=tyke,password=mypassword,noauto,w
```

The problem is it's not mounting as read write, it's mounting as read only. I can write to it as root, but not as a standard user.  One thing I have noticed is that the permissions on the folder it mounts to change when I mount it. It goes from "owner - tyke" to "owner - root".

I have no doubt I'm doing something totally obvious wrong, but I would appreciate it if someone could point out what, because I'm stumped.

Thanks in advance.

---

### Post by joshkidd on 2007-03-01
I think that you want to add "user" to the list of options in your fstab so that it's something like:

```
//study-desk/MyFiles	/home/tyke/server	smbfs username=tyke,password=mypassword,noauto,rw,user
```

The user option allows users other than root to mount the share.

---

### Post by tyke on 2007-03-01
just tried that, makes no difference, I can still only write to it as root.

I can mount it as a normal user, I never had any problems doing that, I just can't write to it as a user.

---

### Post by Eddy Dean on 2007-07-22
Same problem. the relevant bit of /etc/fstab looks like this:

```
//links/Diversen /home/gezin/Diversen smb username=gezin,password=iwonttellyou,uid=g
ezin 0 0
//links/Films /home/gezin/Films smb username=gezin,password=iwonttellyou,uid=gezin 0
 0
//links/Fotos /home/gezin/Fotos smb username=gezin,password=iwonttellyou,uid=gezin 0
 0
//links/Fotos_origineel /home/gezin/Fotos_origineel smb username=gezin,password=
iwonttellyou,uid=gezin 0 0
//links/Muziek /home/gezin/Muziek smb username=gezin,password=iwonttellyou,uid=gezin
 0 0
//links/Office /home/gezin/Office smb username=gezin,password=iwonttellyou,uid=gezin
 0 0
```

And this is the relevant part of /etc/mtab:
```
//links/Diversen /home/gezin/Diversen smbfs rw 0 0
//links/Films /home/gezin/Films smbfs rw 0 0
//links/Fotos /home/gezin/Fotos smbfs rw 0 0
//links/Fotos_origineel /home/gezin/Fotos_origineel smbfs rw 0 0
//links/Muziek /home/gezin/Muziek smbfs rw 0 0
//links/Office /home/gezin/Office smbfs rw 0 0

```

I can read all data from the "server", but I can't remove, modify or create anything. Both computers are ALWAYS logged in as user gezin.

I am sure the shares are shared for read and write access (although I can't confirm that right now, the computer is occupied).

---

