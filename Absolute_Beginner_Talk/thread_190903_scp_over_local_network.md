---
title: "scp over local network"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by macdo on 2006-06-06
Scp is surely overkill on a local network. I should be using NFS, I know.
But...
But I can connect to my brother's PC on the other side of France, and not to my laptop on the other side of the room, with SCP.
Any ideas what I'm missing?
Cheers!

---

### Post by hw-tph on 2006-06-07
The openssh-server package must be installed (and running of course) on the machine you are trying to scp to/from.


Håkan

---

### Post by steve.horsley on 2006-06-07
Another thing:
The first time you ssh to a server, it asks you to confirm the identity, and if you do it saves in a list of known hosts.
If you use the Nautilus GUI to use ssh to a server, and it's the first time you have connected to that server, it dosen't ask you to confirn - it just hangs. So you must ssh to the server by hand and confirm its identity before you can use Nautilus file transfer.

---

