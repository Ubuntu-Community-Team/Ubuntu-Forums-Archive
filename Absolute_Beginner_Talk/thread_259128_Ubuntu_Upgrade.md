---
title: "Ubuntu Upgrade?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-09-16
Can you upgrade ubuntu from like Badger 5.10 to dapper 6.06?:confused:

---

### Post by keithb on 2006-09-16
It would probably be better to do a fresh install.

---

### Post by th3t1nm4n on 2006-09-16
If you want to just upgrade (might break some packages) edit your /etc/apt/sources.list, wherever it says "badger" put "dapper". Then do ```
sudo apt-get update
sudo apt-get dist-upgrade
```
to upgrade to Dapper.
Good Luck.

---

### Post by 3rdalbum on 2006-09-17
That above post should read:

Where it says "breezy", put "dapper".

Dist-upgrading is quite reliable.

---

### Post by th3t1nm4n on 2006-09-19
Yeah, sorry about that, didn't use breezy that long.
Be sure to read this: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

