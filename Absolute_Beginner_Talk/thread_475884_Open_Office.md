---
title: "Open Office"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-16
Where is the best place for me to download open office outside of the repositries (as I am on a proxy connection). When I tried the download from the site, it said that the file type it used was incompatiable so I need another download location.

Thanks,
Ajeffreys

---

### Post by Bachstelze on 2007-06-16
You can very well use apt from behind a proxy :

```
export http_proxy="http://login:password@host:port"
sudo apt-get install openoffice.org
```

---

### Post by ajeffreys on 2007-06-16
I need a username for my proxy though.

So if mine is proxy 2, at port 8080 and than a username and password what do i do?

---

