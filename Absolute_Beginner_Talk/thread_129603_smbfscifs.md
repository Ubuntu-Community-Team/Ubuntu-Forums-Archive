---
title: "smbfs/cifs"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by OTll on 2006-02-14
Hey all,
I'm running into a little problem here... I'm on a network and want to mount Win Server2003 shares. Here's the problem:

```

$ mount -t smbfs //server2003/users /media/users
mount: alleen root kan dat doen

```
only mount can to that... ok, no problem
```

$ smbmount  //server2003/users /media/users
cli_negprot: SMB signing is mandatory and we have disabled it.
14943: protocol negotiation failed
SMB connection failed

```
Now, I don't like that... what's wrong here... Dunno, but no problem, some other stuff to try:
```

$ smbclient //server2003/users
Password:
Domain=[EPAS] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]
smb: \> exit

```
That works, great...
```

$ sudo smbclient //server2003/users
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt

```
but it doesn't work if I try it as root, even if I add the '-U' parameter
```

$ smbclient //server2003/users -U kurt
Password:
Domain=[EPAS] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]
smb: \> exit
$ sudo smbclient //server2003/users -U kurt
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt

```
Now, trying to mount... 
```

$ smbmount  //server2003/users /media/users
cli_negprot: SMB signing is mandatory and we have disabled it.
14961: protocol negotiation failed
SMB connection failed
$ mount -t smbfs  //server2003/users /media/users -o username=kurt
mount: alleen root kan dat doen
$ sudo mount -t smbfs  //server2003/users /media/users -o username=kurt
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt

```
Nothing very new here, only root can mount smbfs-systems, but it doesn't work. And if I try as 'kurt', it has some kind of security-like thing. So, checking some forums, 'cifs' would possibly be a solution:
```

$ sudo mount -t cifs  //server2003/users /media/users -o username=kurt
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt
$ sudo mount -t cifs  //server2003/users /media/users
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt
$ sudo mount -t cifs  //server2003/users /media/users -o user=kurt
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt

```
again the problem that connecting as root doesn't work out very well, so trying as 'ordinary' user:
```

$ mount -t cifs  //server2003/users /media/users -o user=kurt
mount: alleen root kan dat doen

```
Oh yeah, forgot, only root can mount, well, let's try this:
```

$ mount.cifs  //server2003/users /media/users -o user=kurt
mount error: could not find target server. TCP name server2003/users not found  rc = -5011088
No ip address specified and hostname not found

```
Aah, that looks better, something else... but still, no connection: cifs can't find 'server2003' or something?

Anybody can help me out of this?

Thx a lot, OTll

---

### Post by Robgould on 2006-02-14
Check this out....hope it helps you.
 
[http://www.ubuntuforums.org/showthread.php?t=126538]("http://www.ubuntuforums.org/showthread.php?t=126538")

---

### Post by OTll on 2006-02-14
Thx for you answer, but it doesn't really help... fstab tries to mount the smb(cifs?)-share as root (I suppose), and that seems not to work, for one reason or another. I have/had this in my fstab:
```

//SERVER2003/Users/   /media/users    smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

```
In some way, I need to be able to log in as root... but it just doesn't want to work out, so far...

[QUOTE=Robgould]Check this out....hope it helps you.
 
[http://www.ubuntuforums.org/showthread.php?t=126538]("http://www.ubuntuforums.org/showthread.php?t=126538")[/QUOTE]

---

### Post by OTll on 2006-02-16
I can mount network drives now. It didn't work for three reasons:
1/ I had to add the workgroup. 'mount -t cifs' didn't work if I didn't add the workgroup I'm in.
2/ It doesn't work if I do 'sudo mount -t cifs'. However, if I do 'sudo su -' and mount the drives as root, it works out fine. 
3/ I had to use the IP-address with 'cifs'. It's not necessary with smbfs, but I can't mount all drives using smbfs. cifs mounts them all, but I have to point to IP-addresses instead of names.

No problems at all with adding the lines for mounting the network drives in fstab 

OTll

---

