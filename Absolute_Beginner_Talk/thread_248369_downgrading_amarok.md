---
title: "downgrading amarok"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-09-01
today i isntalled the update for amarok and now none of my music files have ID3 tags, does anyone know how i can downgrade to the older version or what the name of the older version package is?

---

### Post by jordanmthomas on 2006-09-01
```

cd /var/cache/apt/archives
ls | grep amarok

```
Maybe the old version is in there and you can install it instead?

---

### Post by shamrock_uk on 2006-09-02
> **cptjaben said:**
> today i isntalled the update for amarok and now none of my music files have ID3 tags, does anyone know how i can downgrade to the older version or what the name of the older version package is?

I noticed in one of the developers blogs that there had been initial problems with the Dapper version. [here](http://www.imbrandon.com/) - 3rd or 4th entry down.

Try deleting the amarok .debs from /var/cache/apt/ and then doing sudo apt-get update and sudo apt-get install amarok

This should get the very latest version

---

