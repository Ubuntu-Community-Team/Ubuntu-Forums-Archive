---
title: "feisty upgrade problems"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by SeaRox on 2007-09-13
I tried using the update manager and sudo apt-get dist-upgrade and I get this error:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/Release](http://archive.canonical.com/ubuntu/dists/edgy-commercial/Release) Unable to find expected entry  restricted/binary-i386/Packages in Meta-index file (malformed Release file?)
I tried updating my sources.list and I read through the "similar threads" but to no avail.
Any help on how to fix this?

---

### Post by mikeyphi on 2007-09-14
If you are trying to do a dist-upgrade on Feisty - you will have to wait until the next official release (Gutsy) due in October.
If this is not what you are trying to do - please restate your problem.

---

### Post by chuckyp on 2007-09-14
Try editing your /etc/apt/sources.list and removing the canonical comercial repo since its not working for you.  Then
```

$ sudo apt-get update && sudo apt-get dist-upgrade

```

---

