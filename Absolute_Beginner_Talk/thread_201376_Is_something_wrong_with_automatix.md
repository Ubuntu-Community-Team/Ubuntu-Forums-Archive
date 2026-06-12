---
title: "Is something wrong with automatix?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by wog on 2006-06-21
I just got a 404 error trying to update to version 6.1-11 of automatix.

W: Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.1-11_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.1-11_i386.deb)

Is this something I can fix, or do I just need to wait for someone else to do something about it?

---

### Post by %hMa@?b&lt;C on 2006-06-21
```
wget http://www.beerorkid.com/automatix/apt/dists/dapper/main/binary-i386/automatix_6.1-13_i386.deb

```
```
sudo dpkg -i automatix_6.1-13_i386.deb
```

---

### Post by wog on 2006-06-21
Thanks. :)

---

