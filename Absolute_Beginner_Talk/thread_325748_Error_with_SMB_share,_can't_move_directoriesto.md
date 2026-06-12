---
title: "Error with SMB share, can't move directoriesto"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Chachee on 2006-12-26
Greetings all,
  I'm running - 

Dapper Drake
Currently Updated

  I've got a FreeNAS server set up at home that I'm trying to copy all my music too.  I have anonymous connections set up so the SMB log shows a user connecting as:

> 192.168.1.100 (192.168.1.100) connect to service Music initially as user ftp (uid=21, gid=50) (pid 382

That's my computer connecting.  I've ripped a CD that I would like to copy to the share.  However I get this error when I try to pull a folder over:

> Error "Not a directory" while copying "/home/jerem...r (disc 1)".

Here's where it gets weird... I can pull over individual files.. no problem.](*,) 

I couldn't find anything in syslog or /log/samba that would help.  Also couldn't find anything on the forum or a quick google.

I can mount the SMB shares, but can't modify any files inside the mounts, even if I chmod 777 the mounted directory.

I'm not really sure what to search for, the error message is too long to really narrow it down.

THank you!

JT

---

