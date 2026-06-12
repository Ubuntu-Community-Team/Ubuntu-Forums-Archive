---
title: "Updating from 6.06 to 6.10 error message - code 2"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-03-20
Hi,
I''m updating 6.06 to 6.10, tried yesterday and ran into some errors.
So, now i'm trying it again, slowly...

I'm using 
```
gksu "update-manager -c"
```
to update.
In terminal i get the following....

```
steve@laptop:~$ gksu "update-manager -c"
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpH_QPYE/edgy.tar.gz'
authenticate '/tmp/tmpH_QPYE/edgy.tar.gz' against '/tmp/tmpH_QPYE/edgy.tar.gz.gpg' 
```

Followed by this error 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Can anybody tell me what i'm doing wrong?

---

### Post by zvacet on 2007-03-20
this is just example
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
Do this with your security and any unofficial repositories and try again

---

### Post by stoer on 2007-03-20
> **zvacet said:**
> this is just example
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
Do this with your security and any unofficial repositories and try again

Thanks for your reply,
I'm now at work so i'll give it a go tonight....
still 7 hrs to go :(
Cheers!

---

