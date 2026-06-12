---
title: "Upgrade to 6.10??"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2007-01-23
How do I upgrade from Ubuntu 6.06 to 6.10

Thanks!

---

### Post by dbbolton on 2007-01-23
there are threads all over on how to do this...

```
 sudo apt-get update
sudo apt-get dist-upgrade
```


but, i severely advise against it. i did it, and on another computer, i backed up my files from the dapper partition to a dvd, erased the partition, and did a clean install of edgy. i recommend the latter.

---

### Post by aysiu on 2007-01-23
```
sudo apt-get update && sudo apt-get dist-upgrade
``` won't upgrade you to Edgy unless you first edit your /etc/apt/sources.list and change all the *dapper*s to *edgy*s.

---

### Post by spyker3292 on 2007-01-23
didnt work, doesnt matter ill do it some other time

(isnt 6.06 edgy?)

---

### Post by aysiu on 2007-01-23
6.06 is Dapper
6.10 is Edgy

---

### Post by Tux Aubrey on 2007-01-23
There is an upgrade guide here:

[https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")

I recently used the **gksu "update-manager -c" ** method on my "production" machine (after backing up my data files) and it went very smoothly.

---

