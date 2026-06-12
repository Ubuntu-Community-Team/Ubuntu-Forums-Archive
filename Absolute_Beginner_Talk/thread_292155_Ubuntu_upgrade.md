---
title: "Ubuntu upgrade"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2006-11-03
Hi guys,

Is there a way to upgrade my version of Ubuntu from 6.06 to 6.1 without having to do a complete re-install. I tried the update manager, but I don't think it did the full upgrade.

Thanks in advance guys!!! Linux newbie here, obviously!

---

### Post by Iarwain ben-adar on 2006-11-03
Hi,
to completely upgrade,
change all instances of 'dapper' to 'edgy' in your /etc/apt/sources.list

and then type
```
sudo aptitude upgrade
```


Iarwain

---

### Post by Stone9 on 2006-11-04
Great! Exactly what I was looking for :)

---

### Post by taurus on 2006-11-04
> **Iarwain ben-adar said:**
> Hi,
to completely upgrade,
change all instances of 'dapper' to 'edgy' in your /etc/apt/sources.list

and then type
```
sudo aptitude upgrade
```


Iarwain
I am sorry but that is not the way to upgrade from Dapper to Edgy!  If you do that, you could have a head Edgy...  The right way is to follow this instruction!

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Iarwain ben-adar on 2006-11-05
Sorry,
didn't know about that one :?


Iarwain

---

