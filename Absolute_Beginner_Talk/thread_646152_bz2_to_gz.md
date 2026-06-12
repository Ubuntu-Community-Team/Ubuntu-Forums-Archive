---
title: "bz2 to gz"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by wingfin on 2007-12-20
how do i convert a tar.bz2 to a  tar.gz?

---

### Post by chips24 on 2007-12-20
extract it, right click it, press archive folder and press tar.gz, why?

---

### Post by nick_h on 2007-12-21
From the command line you could use bzcat and gzip to decompress and then recompress the file.
```
bzcat file.tar.bz2 | gzip > file.tar.gz
```

---

