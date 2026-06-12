---
title: "NFS service not starting up!! :O :S"
date: 2006-08-31
forum: Apple PPC Users
---

### Post by dragze on 2006-08-31
Hi all, i have installed nfs-common and all dependencies on two pc's and they have all worked fine, no problem and no extra configuration, install nfs on an old imac (500mhz) and the service wont start :O :S.

I dont have a clue why it wont start had a look through some logs and the only thing i could see was in dmesg which gave:
> [  108.935614] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[  109.799130] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  109.802819] NFSD: recovery directory /var/lib/nfs/v4recovery doesn't exist
[  109.802848] NFSD: starting 90-second grace period


Which means nothing to me?? so plz somebody tell me why this isnt starting.

If u need any more info just ask!

Thanks in advance,
dragze.

---

### Post by dragze on 2006-08-31
anybody?? somebody?? please!!! 

i really am stuck with this one and i really really need it to work cause this machine is supposed to be hosting files to other linux boxs on the network!

please please please help!! :D

Thanks in advance,
dragze.

---

### Post by calum on 2006-09-01
> **dragze said:**
> anybody?? somebody?? please!!! 

i really am stuck with this one and i really really need it to work cause this machine is supposed to be hosting files to other linux boxs on the network!

please please please help!! :D

Thanks in advance,
dragze.

Are you using the kernel or userspace NFS server?  Does it work if you start it manually, or is it not working at all?

---

### Post by boast on 2007-11-29
I have the same problem.

Sometimes NFS starts up fine on boot, and sometimes it does not.

It works fine when started manually. 

My NFS server shows this ```
mountd[2784]: authenticated mount request from ubox.BBNET:669 for /home/media (/home/media)
``` so it should of loaded normally. It is no different then when I manually remounted ```
mountd[2784]: authenticated mount request from ubox.BBNET:1019 for /home/media (/home/media)
```

---

