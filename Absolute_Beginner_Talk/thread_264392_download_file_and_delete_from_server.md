---
title: "download file and delete from server"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Miademora on 2006-09-24
Hello,

how may i automatically download a file and delete it from server after successful transfer?

Im not finding the correct options in scp or rsync(d).

Is there a tool wich does that?

Thanks in advance!

---

### Post by kidders on 2006-10-03
Hi there,

SCP (secure cp) is really for copying, not moving, just like rsync. Moving things is mostly only supported by more elabourate filesharing protocols, like NFS, Samba, AFP, etc.

---

