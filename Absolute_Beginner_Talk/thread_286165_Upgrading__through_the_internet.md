---
title: "Upgrading  through the internet"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by truNWA on 2006-10-27
I use Dapper drake but i would like to upgrade to Edgy. How would i go about this without actually having to download any cd's?

---

### Post by PriceChild on 2006-10-27
[COLOR=Red]**You do this at your risk!!!**[/COLOR]```
sudo update-manager -c
```

---

### Post by trippyd on 2006-10-27
Ubuntu Documentation to the rescue!

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Easy as pie.

---

### Post by John.Michael.Kane on 2006-10-27
[COLOR="Red"]**You do this at your risk!!!**
[/COLOR]

```
sudo aptitude update && sudo aptitude upgrade
```

```
gksudo "update-manager -c -d"
```

OR

```
sudo gedit /etc/apt/sources.list
```
replace all the words that have dapper to edgy

Then run these:
```
sudo aptitude update 
sudo aptitude dist-upgrade
```

---

