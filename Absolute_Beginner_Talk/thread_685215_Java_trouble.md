---
title: "Java trouble"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by AutumnPhoenix on 2008-02-01
>  Setting up sun-java-5-doc (1.5.0-13-0ubuntul) ...
This package is an installer package, it does not actually contain the J2SDK document.  You will need to download one of the archives:

jdk-1_5_0-doc.zip           jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  This file should be owned by root.root and be copied to /tmp.



I downloaded its in tmp but it has myself as the owner


it still won't work

---

### Post by dcstar on 2008-02-02
> **AutumnPhoenix said:**
> I downloaded its in tmp but it has myself as the owner


it still won't work

```
chown root filename
chgrp root filename
```

---

