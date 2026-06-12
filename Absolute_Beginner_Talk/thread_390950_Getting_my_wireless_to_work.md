---
title: "Getting my wireless to work"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-22
When I go to the Network Manager, I see **ra0** there, however, when I enter my ESSID (I'm on a open network) and activate it, I still don't have a internet connection. What should I do? Please help this newbie out. :)

---

### Post by bapoumba on 2007-03-22
> **.oops said:**
> When I go to the Network Manager, I see **ra0** there, however, when I enter my ESSID (I'm on a open network) and activate it, I still don't have a internet connection. What should I do? Please help this newbie out. :)
Please open a terminal (> Accessories > Terminal) and give the output to:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig
```

---

### Post by .oops on 2007-03-22
I would if I was in Ubuntu right now, but I have to reinstall it. )x It won't boot now. Sorry I couldn't be more helpfull. I'll post the output later.

---

