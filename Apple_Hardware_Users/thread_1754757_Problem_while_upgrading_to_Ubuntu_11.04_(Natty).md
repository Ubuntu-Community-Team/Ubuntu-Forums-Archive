---
title: "Problem while upgrading to Ubuntu 11.04 (Natty)"
date: 2011-05-10
forum: Apple Hardware Users
---

### Post by MizoZ on 2011-05-10
Hi,

I'm using an iBook G4 (1.33) PowerPC. I wanted to upgrade to the newest ubuntu which is Natty Narwhal , but I can't. A problem happens while the upgrading tool fetches new packages, here's the errors :

```

W:Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```Could someone help me please ?

Regards.

---

### Post by avtolle on 2011-05-11
Try disabling the partners repository in Software Sources, refreshing, and give it another try. This has worked for me on upgrades from 9.10 to 10.04, and 10.04 to 10.10. YMMV.

---

### Post by MizoZ on 2011-05-11
It works, thanks a lot :D

---

