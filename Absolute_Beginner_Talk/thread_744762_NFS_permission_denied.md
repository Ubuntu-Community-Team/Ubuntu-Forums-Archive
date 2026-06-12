---
title: "NFS permission denied"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by prem1er on 2008-04-03
Just set up a NFS server on an ubuntu desktop.  I set up the NFS client on my laptop also running ubuntu gutsy.  When I try to connect to the drive I get the error.  Thanks in advance.

> mount.nfs: 192.168.1.102:share failed, reason given by server: Permission denied

Here is my /etc exports file.


```
  GNU nano 2.0.6             File: /etc/exports                                 

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
share 192.168.1.100(rw,no_root_squash,async)


```


And here is my /etc/hosts.allow

```
portmap: ALL
lockd: ALL
mountd: ALL
rquotad: ALL
statd: ALL

```

---

### Post by prem1er on 2008-04-04
bump...

---

### Post by The Titan on 2008-04-04
where is the "share" folder located? it should be a direct path like home/username/share or whatever.



 then to mount it do 

```

mount 192.168.0.102:/home/username/share /wherever/to/mount

```

---

