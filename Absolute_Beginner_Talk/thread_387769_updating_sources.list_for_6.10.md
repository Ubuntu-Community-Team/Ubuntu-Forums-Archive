---
title: "updating sources.list for 6.10"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-03-18
I am running Ubuntu 6.06 on my PowerBook G3 Wallstreet (Old World).  I want to use the Update Manager to upgrade to Ubuntu 6.10.  The 'Upgrade' choice is not given, so I have heard that I can instead edit something in the sources.list.  Can I use the sources.list generator ([http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/"))?
I am told that I change dapper to edgy, but I am kind of hesitant.  So, can anyone describe in detail how to edit the sources.list file?

Thanks

---

### Post by taurus on 2007-03-18
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by DougieFresh4U on 2007-03-18
Bring up your sources list and change all dapper to edgy and then select save from the file menu.  Then close and run **sudo apt-get update && sudo apt-get upgrade** hope this works out for you as it's not considered the "official" way of doing it.

---

### Post by taurus on 2007-03-18
> **DougieFresh4U said:**
> Bring up your sources list and change all dapper to edgy and then select save from the file menu.  Then close and run **sudo apt-get update && sudo apt-get upgrade** hope this works out for you as it's not considered the "official" way of doing it.

Actually, it should be (if you _really_ want to go that route)

```
sudo aptitude update
sudo aptitude **dist-upgrade**
```

---

### Post by mdknaebel on 2007-03-18
> **DougieFresh4U said:**
> Bring up your sources list and change all dapper to edgy and then select save from the file menu.  Then close and run **sudo apt-get update && sudo apt-get upgrade** hope this works out for you as it's not considered the "official" way of doing it.

so, do i just change any word that is dapper to edgy? or do i have to do more?

---

### Post by DougieFresh4U on 2007-03-18
> **taurus said:**
> Actually, it should be (if you _really_ want to go that route)

```
sudo aptitude update
sudo aptitude **dist-upgrade**
```

Thanks for correcting that as I thought that might be the the way  :)

---

### Post by taurus on 2007-03-18
> **DougieFresh4U said:**
> Thanks for correcting that as I thought that might be the the way  :)

The way to upgrade from Dapper to Edgy is not to modify /etc/apt/sources.list.  Instead, should go with the official method.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by DougieFresh4U on 2007-03-18
> **mdknaebel said:**
> so, do i just change any word that is dapper to edgy? or do i have to do more?

Yes, change all dapper to edgy and save then run codes posted in above post. Let us know how you come out.:) (that is called the "hacky" way)

---

### Post by mdknaebel on 2007-03-18
Well, actually, I got the Upgrade choice to come up afterall

Thanks!

---

