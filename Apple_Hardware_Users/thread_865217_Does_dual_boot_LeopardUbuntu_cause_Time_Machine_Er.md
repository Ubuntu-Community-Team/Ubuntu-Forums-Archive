---
title: "Does dual boot Leopard/Ubuntu cause Time Machine Error?"
date: 2008-07-20
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-07-20
Hi,
I'm dual booting Leopard/Hardy on a 24" aluminum iMac. Every so often, on the Mac OS side, I'm getting a generic Time Machine error that says something like:

> Time Machine has encountered an error during backup

I can't remember if it says anything else. But I checked my Time Machine and I DO have backups for the last few weeks which is about right.

I'm using a LaCie hard drive that goes in firewire. My only guess is that the Time Machine might be encountering rEFIt or something about the partitioned drive and it causes an error to occur.

Has anyone else encountered this? I appreciate any feedback...

Many Thanks, Frank B.

---

### Post by schauerlich on 2008-07-21
That error doesn't seem related to Ubuntu. Time Machine should only look at Macintosh HD, and therefore won't concern itself with any other partitions you may have.

---

### Post by Brightbelt on 2008-07-21
Many Thanks Dave.

---

### Post by cyberdork33 on 2008-07-21
I concur. Corrputed file on the backup or something... I would run a check on the external drive to make sure everything is OK, then maybe start a new time machine backup. There might be some solutions out there, but I don't see anything for your particular problem. I usually see that error when starting a backup, but that is because I use a samba share as my time capsule.

---

### Post by Brightbelt on 2008-07-22
Thanks Cyber.

---

