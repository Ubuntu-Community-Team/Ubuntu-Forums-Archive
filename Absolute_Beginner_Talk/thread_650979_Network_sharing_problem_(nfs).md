---
title: "Network sharing problem (nfs)"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Sheix on 2007-12-27
Well, i'm not absolute beginner, but looks like problem is too simple and i made it too complicated for me...

Have two Ubumtu 7.10 pc's 
1st - laptop connected to router edimax with wireless (broadcom43xx) got ip 192.168.2.101
2nd - wired (don't remember exactly driver) got ip 192.168.2.102

have to share my home directory to rw access

Installed nfs services as explained ([http://ubuntuforums.org/showthread.php?t=193408](http://ubuntuforums.org/showthread.php?t=193408)) on boths machines, restarted them, tried to mount -> nothing. used mount, mount.nfs, mount.nfs4. checked /etc/exports. it's as described. pings between two machines ok. I still cann't see shared folders.

When i open places -> network i see only windows network icon (configured smb from before), but cann't see the shared pc's hard drives/shared folders. Tried places -> connect to server (this is mount, right?) same, cann't connect. 

I'm really depressed about this...

What i'm doing wrong?
What's wrong with me???

Thanxx in advance...

---

### Post by bodhi.zazen on 2007-12-27
What is your mount point ?

Try this :

On 192.168.2.102

```
sudo mkdir /media/share
sudo mount 192.168.2.101:/home/user_name /media/share
```

Now, list /media/share

```
ls /media/share
```

---

### Post by Sheix on 2007-12-27
Oh, thank you! I dont' even had an idea how to continue. Tried this, but may be done something wrong
so:

```

sheix@sheix-desktop:~$ sudo mkdir /media/laptop
[sudo] password for sheix:
sheix@sheix-desktop:~$ sudo mount 192.168.2.100:/home/sheix /media/laptop
mount.nfs: mount to NFS server '192.168.2.100' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.2.100' failed: timed out, retrying

```

and so on...

went to another pc closed firestarter (in another OSes they may cause such problems)
checked ip's and sharing folders, restarted all daemons...

```

sheix@sheix-desktop:~$ sudo mount 192.168.2.100:/home/sheix /media/laptop
mount.nfs: 192.168.2.100:/home/sheix failed, reason given by server: Permission denied

```

got something better, as i see.

Set (rw) at the end of the line in the  /etc/exports, restarted daemons again. Same story.
Tried to add IP of allowed hosts there -> without any changes too.

I thing that the reason is something wrong in my /etc/exports file, so there it is

```

/home/anton  192.168.2.101 (rw)

```

and... I realized that i've done such a stupid mistake... Wrong directory name :)

Thank you so much, really helped me. And it was easy :)

---

