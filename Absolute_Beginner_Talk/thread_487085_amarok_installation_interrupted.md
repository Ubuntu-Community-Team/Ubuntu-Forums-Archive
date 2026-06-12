---
title: "amarok installation interrupted"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by viralbug on 2007-06-28
i just installed ubuntu (wubi installation) and am a complete newbie.
i was installing amarok using the command: sudo apt-get install amarok

while installing i goofed up something and the installtion was stopped. :oops: so i used the same command again but now it gives this error.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

so i ran the command but it gives this error.
dpkg: requested operation requires superuser privilege

im the only user so why does it say it requires superuser privelage?

i tried to install another software but it still gives the same error. :confused:

---

### Post by shearn89 on 2007-06-28
Linux automatically creates your user as a general user, not an admin with write-privileges to system files. This message is just telling you to put "sudo" before the command - it stands for "super-user do", and should let you run the command, thereby allowing you to reinstall!

---

### Post by viralbug on 2007-06-28
oh ok. so thats what sudo means.
thanks a lot! :)

---

### Post by shearn89 on 2007-06-28
no probs - post back if you still have probs, although i'm off on holiday tomorrow. Someone else should be able to help though...

---

