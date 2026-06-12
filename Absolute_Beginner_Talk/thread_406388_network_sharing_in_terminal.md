---
title: "network sharing in terminal"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-04-10
how do i share files using a terminal? I already know how in x but i cant get ino x for various reasons, and i need to share some files.

---

### Post by devnulljp on 2007-04-11
You just wantto copy files from one machine to another? 
Use rsync or scp

scp file-to-copy [email]username@remote.machine.dns.name.or.ip[/email]:directory
copy whole directory:
scp -r dir-to-copy [email]username@remote.machine.dns.name.or.ip[/email]:directory

Use rsync for incremental copies

---

