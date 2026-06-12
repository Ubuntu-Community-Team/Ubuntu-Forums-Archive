---
title: "Any recommendation of the repository sources for ppc?"
date: 2006-07-11
forum: Apple PPC Users
---

### Post by Najand on 2006-07-11
Does anyone has a recommendation of the repository sources for ppc? I am working on an ibook G4 and using dapper drake for ppc; unfortunately the only sources I have is:

```

# Ubuntu official CD for Dapper Drake
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release powerpc (20060531)]/ dapper main

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse


```

---

### Post by 3rdalbum on 2006-07-11
Add:

```

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

```

I think there's only one third-party PPC repository, and the last time I added it to my iMac's sources.list, it didn't respond.

---

### Post by Najand on 2006-07-12
> **3rdalbum said:**
> Add:

```

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

``` 
I think there's only one third-party PPC repository, and the last time I added it to my iMac's sources.list, it didn't respond.

Thank you very much for your reply. The BackPort Respository is not working for a long time. I think these are the only ones available at the moment.

---

