---
title: "Zlib"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2007-04-01
Ubuntu Server 6.10

Trying to install gpac so I can encode MP4 with FFMPEG and it's asking for ZLIB, which doesn't seem to be in the reposatories?

Where can I apt-get this from?

---

### Post by yabbadabbadont on 2007-04-01
It is probably called: ```
zlib1g
```  At least it is on Dapper.  Try searching with aptitude to see what it is on Edgy: ```
aptitude search zlib
```

---

