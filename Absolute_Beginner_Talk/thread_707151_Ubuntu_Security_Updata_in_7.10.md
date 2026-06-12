---
title: "Ubuntu Security Updata in 7.10"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by -Abid- on 2008-02-25
well i installed ubuntu 7.10 just hours frm now and i went to update my ubuntu but when i click check it says ur system is up to date! how can that be possible when i was runing 7.04 ther was about 239.9 mb of update.... what am i doing wrong?

---

### Post by kesman on 2008-02-25
check the software sources and apply every one of them under system -> administration -> software sources . After this, try again, or in terminal you could try
```

sudo apt-get update
sudo apt-get dist-upgrade

```
if this doesn't give you any updates, then I would say you have an up-to-date system.

---

### Post by -Abid- on 2008-02-25
thanx that did the trick =D>

---

