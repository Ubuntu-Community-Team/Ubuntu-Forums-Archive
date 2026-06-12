---
title: "Will updates turn fiefty into gutsy?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by svriderpokey on 2007-10-03
Or will I have to reinstall to upgrade?

---

### Post by pay on 2007-10-03
You will need to specifically tell the update manager to update to Gutsy. either by changing your sources.lst to a gutsy one or by issueing ```
sudo aptitude update
sudo update-manager --devel-release --proposed --dist-upgrade
```Obviously remove the options that you don't want.

---

### Post by thiebaude on 2007-10-03
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Paulmd on 2007-10-04
> **pay said:**
> You will need to specifically tell the update manager to update to Gutsy. either by changing your sources.lst to a gutsy one or by issueing ```
sudo aptitude update
sudo update-manager --devel-release --proposed --dist-upgrade
```Obviously remove the options that you don't want.



sudo update-manager -d 

is a bit shorter :)

---

### Post by RomeReactor on 2007-10-04
Hi. If I'm not mistaken, when Gutsy comes out Oct. 18, the update manager will notify you that there's a new version of Ubuntu and if you would like to upgrade to it.

---

### Post by viper on 2007-10-04
> **RomeReactor said:**
> Hi. If I'm not mistaken, when Gutsy comes out Oct. 18, the update manager will notify you that there's a new version of Ubuntu and if you would like to upgrade to it.

That would be correct...

---

### Post by pay on 2007-10-04
> **Paulmd said:**
> sudo update-manager -d 

is a bit shorter :)But it doesn't explain the options.:)

---

