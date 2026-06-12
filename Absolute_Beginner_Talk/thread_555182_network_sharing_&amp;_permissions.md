---
title: "network sharing &amp; permissions"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-09-19
I want to transfer large files from my ubuntu laptop to ubuntu desktop b/c I want to reinstall Feisty on the laptop with separate partitiions for home and OS.  I have samba working (some XP's on home lan) and can share files.  However, if I share a Photos file the desktop can't open the contained folders and files b/c permissions allowed on the Photos folder don't extend to the contained files.  How can I give permission to open all contents of the larger Photos file?  Is there some other way to transfer the big files over network?
Thanks.

---

### Post by Bushfire on 2007-09-19
Try this:
```
$ sudo chmod -Rv a+rx Photos
```

---

