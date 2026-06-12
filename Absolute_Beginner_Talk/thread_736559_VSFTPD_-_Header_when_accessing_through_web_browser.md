---
title: "VSFTPD - Header when accessing through web browser"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Meson on 2008-03-26
I'm running vsftpd and when I access the site through a web browser it says "Index of...."

I notice some sites are able to add some text up there before the directory listing.  How do I do that?

---

### Post by spydon on 2008-03-28
Try to add this in your vsftpd.conf file:
```
ftpd_banner="My banner"
```

---

