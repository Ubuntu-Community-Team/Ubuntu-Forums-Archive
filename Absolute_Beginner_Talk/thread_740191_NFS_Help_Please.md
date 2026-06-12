---
title: "NFS Help Please"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-30
```
titan@dungeon$ sudo mount  192.168.0.2:/srv/quake3 /home/titan/quake_server -o nolocks
mount.nfs: Unsupported nfs mount option: nolocks

```

thats what i get when i try to mount my nfs, it all worked fine until i added the last share to exports

```
root@temple:/srv# cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
#
# Example for NFSv4:
#
/var/www 192.168.0.3(rw,no_root_squash,sync)
/sys_backup 192.168.0.3(rw,no_root_squash,sync)
/srv/quake3 192.168.0.3(rw,no_root_squash,sync)

root@temple:/srv#            
```

---

