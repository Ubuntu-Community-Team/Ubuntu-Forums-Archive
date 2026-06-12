---
title: "Share DVD/RW over network"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-12-21
I currently have multiple folders shared over my home network mostly serving a media system.

I would like to share my servers DVD/RW with the media client, how would I do this, I tried nfs but it said that media/cdrom0 didn't support nfs export.

server ip is 192.168.1.9 and media ip is 192.168.1.6.

Thanks

---

### Post by puccaso on 2007-12-21
do the following, 


sudo -s

nano -w /etc/samba/smb.conf

then browse down to the section talking about cdroms

there is a ready made script avaliable, to share cdroms/dvds on the network when mounted locally.

hope it helps.

---

