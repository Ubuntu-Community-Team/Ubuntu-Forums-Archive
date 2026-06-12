---
title: "cannot upgrade to edgy!"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-02-24
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/Release.gpg](http://www.getautomatix.com/apt/dists/dapper/Release.gpg) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29). - connect (111 Connection refused)

update manager stops at this ^:confused::confused::confused:

---

### Post by taurus on 2007-02-24
The site has been down for days now so you need to comment out by placing a # in front of it.

```
gksudo gedit /etc/apt/sources.list
```

---

