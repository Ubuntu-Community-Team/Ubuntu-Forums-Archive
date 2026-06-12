---
title: "NFS (With SSH Tunneling)"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-08-04
So I' trying to mount my NFS share from a remote location, with no success so far. 

I based what I've done so far on [this]("http://www.howtoforge.com/nfs_ssh_tunneling") guide. I did not follow it word for word as I have done some SSH Tunneling before and did not think it would be too hard. I was wrong! However I still do not see why I have to do some of the things in that guide.

I already had NFS setup on my server.
/etc/exports:
```

/home 192.168.0.1/24(rw,async,no_root_squash)

```

Added this to /etc/default/nfs-common:
```

STATDOPTS=--port 2231

```

Added this to /etc/modules:
```

options lockd nlm_udpport=2232 nlm_tcpport=2232

```

And added this to /etc/default/nfs-kernel-server:
```

RPCNFSDCOUNT=8
RPCMOUNTDOPTS='-p 2233'

```

Also added this to grub
```

lockd.udpport=2232 lockd.tcpport=2232

```

Did a restart!

Then on the remote machine in two terminals
```

$ ssh myip -L 61001:localhost:2049    |    $  ssh myip -L 62001:localhost:2233

```

Then in another terminal did and got:
```

sudo mount 127.0.0.1:/home tmp
mount to NFS server '127.0.0.1' failed.

```

Where am I going wrong?

---

### Post by TBerben on 2007-08-04
Can you post the contents of your /etc/hosts.allow and /etc/hosts.deny files please?

---

### Post by guysmiley25 on 2007-08-05
I have nothing configured in those files.

---

### Post by guysmiley25 on 2007-08-11
Bump

---

### Post by guysmiley25 on 2007-09-01
Anyone got any ideas?

---

### Post by guysmiley25 on 2007-09-22
Bump!

---

