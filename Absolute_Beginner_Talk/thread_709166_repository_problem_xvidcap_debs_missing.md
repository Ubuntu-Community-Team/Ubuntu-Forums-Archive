---
title: "repository problem? xvidcap debs missing"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by zoubidoo on 2008-02-27
apt isn't finding xvidcap although the package is in multiverse and multiverse is in my sources.

A quick browse to here shows that the debs are missing.  Other packages have the debs in the same directory.
 [http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcap/](http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcap/)

Could there be a problem with the repository?

---

### Post by Cope57 on 2008-02-27
Seems to be working now...

I do not know where the debs are, but you could compile a deb.
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by zoubidoo on 2008-02-27
> **Cope57 said:**
> Seems to be working now...


Can you see any debs in the link I supplied above?

Shouldn't have to compile if it's supposed to be in the repositories.

---

### Post by zoubidoo on 2008-02-27
Ah, it seems it fails to build from source since dapper, so I guess it isn't included.

[https://bugs.launchpad.net/ubuntu/+source/xvidcap/+bug/120003](https://bugs.launchpad.net/ubuntu/+source/xvidcap/+bug/120003)

---

