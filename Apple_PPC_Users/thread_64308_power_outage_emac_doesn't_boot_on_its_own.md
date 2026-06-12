---
title: "power outage emac doesn't boot on its own"
date: 2005-09-10
forum: Apple PPC Users
---

### Post by sobers_2002 on 2005-09-10
hi

ppc isn't bootin on after a power outage. any tips to get it working right?/

thanx
Saurabh

EDIT:- problem solved.
just do ```
echo server_mode=1 > /proc/pmu/options
```

---

