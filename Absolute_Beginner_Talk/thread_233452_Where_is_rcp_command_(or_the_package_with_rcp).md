---
title: "Where is rcp command (or the package with rcp)?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-10
I read about rcp command but I can't seem to find it with the locate command. Neither can I find it in any package at packages.ubuntu.com.

Please advise.

Thanks.

---

### Post by Iowan on 2006-08-10
Check SSH for similar (secure) command (scp).

---

### Post by Akhran on 2006-08-10
I've installed OpenSSH on my PC. If I'm connecting to ServerA, do I need to install OpenSSH on that server too?

Thanks a bunch !

> **Iowan said:**
> Check SSH for similar (secure) command (scp).

---

### Post by cwaldbieser on 2006-08-10
> **Akhran said:**
> I've installed OpenSSH on my PC. If I'm connecting to ServerA, do I need to install OpenSSH on that server too?

Thanks a bunch !

The remote computer needs an ssh server.  The client technically only needs an ssh client (such as PuTTY).

---

