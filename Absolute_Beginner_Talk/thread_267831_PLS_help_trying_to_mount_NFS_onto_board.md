---
title: "PLS help trying to mount NFS onto board"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-29
I have installled nfs-kernel-server, nfs-common, portmap abd its dependancies in order to get NFS up and running. The word in red "SM01" below is the name of a fingerprint identifiation board that I'm trying to communicate with via my desktop PC (Ubuntu PC). The command that I typed out does not work. How can I solvet this problem.The error is in Green

```
[root@[COLOR="Red"]SM01[/COLOR] /root]$mount -t nfs host:/nfsshare /mnt/nfs
[COLOR="Lime"]mount: can't get address for host
[/COLOR]

```

Oh by the way I also tried :

```
[root@SM01 /root]$mount -t nfs-kernel-server host:/nfsshare /mnt/nfs
[COLOR="Lime"]kmod: failed to exec /sbin/modprobe -s -k nfs-kernel-server, errno = 2
mount: fs type nfs-kernel-server not supported by kernel[/COLOR]
```

---

### Post by bluefrog on 2006-09-29
a wild guess, have you tried:

mount -t nfs sm01:/nfsshare /mnt/nfs

In any case replace host by the name (or ip might work) with the one of the machine hosting the nfs share

James

---

