---
title: "problem is the with keys ..."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-02-25
when i run>  sudo aptitude update
this pwoblem appears , i think the problem is the with keys ::

> W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) edgy-backports Release: Unknown error executing gpgv
W: GPG error: [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) edgy-updates Release: Unknown error executing gpgv
W: GPG error: [http://www.elisanet.fi](http://www.elisanet.fi) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://ubuntu.geole.info](http://ubuntu.geole.info) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BC40ED2499419355
W: GPG error: [http://ubuntu.geole.info](http://ubuntu.geole.info) edgy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BC40ED2499419355
W: GPG error: [http://eyagi.bpa.nu](http://eyagi.bpa.nu) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0027CEFA4B6E7209
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: You may want to run apt-get update to correct these problems

---

### Post by Mornedhel on 2007-02-25
"Unknown error executing gpgv" -> you might want to reinstall gpg. Try getting the package directly from packages.ubuntu.com .

---

### Post by jvc26 on 2007-02-25
What is the output of:
```

cat /etc/apt/sources.list

```
And yes, it looks like you're lacking the gpg keys for the repos mentioned.
Il

---

