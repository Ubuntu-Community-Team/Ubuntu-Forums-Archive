---
title: "Problems upgrading to 9.10"
date: 2009-11-19
forum: Apple Hardware Users
---

### Post by shawnhcorey on 2009-11-19
I start my Update Manager and click on the Upgrade button.  During the process, I get the  following error:
```
W:Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/karmic/Release
Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```

How do I fix this?

---

### Post by avtolle on 2009-11-19
Disable the partner repository in Software Sources and try again (worked for me).

---

### Post by shawnhcorey on 2009-11-19
Thanks, that seems to have worked.

---

### Post by rjcalifornia on 2009-11-21
I have a question: Is there any killer app or update that will make necessary to upgrade to 9.10?

---

### Post by Bazabaza on 2009-12-06
This is happening to me. But partners are already disabled?

---

