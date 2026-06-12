---
title: "mounting remote filesystem using NFS takes too long on boot time"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by s0lid on 2005-10-11
I'm having a problem in hoary using NFS to mount remotely a folder on my NFS server. My NFS server is running on mandrake 9.1 and my workstation is running on ubuntu hoary 5.10 on AMD64.

here's the syntax i added on my /etc/fstab
192.168.0.1:/remote_folder /mnt/home_folder nfs rw,hard,intr 0 0

here's the logs in my /var/log/messages

Oct 11 19:20:20 fat8 kernel: nfs warning: mount version older than kernel
Oct 11 19:20:20 fat8 kernel: portmap: server localhost not responding, timed outOct 11 19:20:20 fat8 kernel: RPC: failed to contact portmap (errno -5).
Oct 11 19:20:20 fat8 kernel: portmap: server localhost not responding, timed outOct 11 19:20:20 fat8 kernel: RPC: failed to contact portmap (errno -5).
Oct 11 19:20:20 fat8 kernel: lockd_up: makesock failed, error=-5
Oct 11 19:20:20 fat8 kernel: portmap: server localhost not responding, timed outOct 11 19:20:20 fat8 kernel: RPC: failed to contact portmap (errno -5).
Oct 11 19:20:20 fat8 kernel: NET: Registered protocol family 10
Oct 11 19:20:20 fat8 kernel: Disabled Privacy Extensions on device ffffffff8035

---

