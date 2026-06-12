---
title: "Creating a &quot;global&quot; FTP connection"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by DrQuincy on 2007-04-27
In OS X I can connect to a server via Samba, FTP, etc and it shows up in Finder so I can access it through my PHP editor.  Can I do something similar via FTP on Linux?

---

### Post by drega on 2007-04-27
> **DrQuincy said:**
> In OS X I can connect to a server via Samba, FTP, etc and it shows up in Finder so I can access it through my PHP editor.  Can I do something similar via FTP on Linux?
you can mount samba shares and navigate to them with an application. I'm not sure about mouting an ftp directory I'm sure it's possible, maybe fuse has a filesystem that could help similar to sshfs (I'm prolly way off track there). 


-Derek

---

### Post by DrQuincy on 2007-04-28
It's okay I figured it out.  You just do Connect to Server... in Nautilus and choose FTP (login).

Thanks.

---

