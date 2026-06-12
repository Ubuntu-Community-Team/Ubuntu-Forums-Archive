---
title: "grsync synchronizing via NAS"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2007-03-21
I have a laptop and a desktop. They are not both on at the same time.
I have an NAS which I can sync to from the laptop, then next day sync the desktop with the NAS.

The NAS has a samba server on it - but I am not sure what command to give my computers to update the NAS and update themselves from it.
I can FTP to the NAS, but don't know how to rsync.

I got grsync and told it
>>smb://192.168.0.1/jon/
as the address for the NAS
But it gives this error>>
ssh: smb: Name or service not known

What do I tell grsync to find the NAS on the network, please?

---

