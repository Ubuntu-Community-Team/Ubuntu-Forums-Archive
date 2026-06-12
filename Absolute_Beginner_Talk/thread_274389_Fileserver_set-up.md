---
title: "Fileserver set-up"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by wootz on 2006-10-09
I finished setting up my fileserver with software RAID5 and LVM and I was wondering if there were any best practices on places to mount my ~900GB storage partition.  Somewhere under /mnt or /media or some place else?  I was planning on having this be a big public storage area for my LAN users serving windows machines via Samba and linux machines via NFS.

-Mike

---

### Post by nix4me on 2006-10-09
I have my shared mounts mounted under /mnt.  Such as /mnt/mp3 or whatever you want to name it/them.

nix4me

---

