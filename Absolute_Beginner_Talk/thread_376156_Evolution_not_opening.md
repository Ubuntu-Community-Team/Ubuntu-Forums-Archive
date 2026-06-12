---
title: "Evolution not opening"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by gezz on 2007-03-04
I'm running Evolution 2.6 on Dapper. After installing Celestia, a graphic-intensive astronomy software, Evolution doesn't open any more. 

I tried re-installing Evolution, then uninstalling Celestia and re-installing Evolution, but no joy.

After trying to start Evolution and doing a ps on the terminal, I find that "/usr/lib/evolution/evolution-dat(a-server-1.6)" and "/usr/lib/evolution/2.6/evolution" are open.

When I try starting Evolution in the terminal, I get the following message: "camel-WARNING **: Failed to initialize NSS"

What does it all mean? What have I broken? How can I fix it?

Many thanks for any help.

Cheers,
Gerald.

---

### Post by bapoumba on 2007-03-04
Try to upgrade your system:
```
sudo aptitude update
sudo aptitude upgrade
```
There was a bug a couple days ago, but it got fixed.

---

### Post by gezz on 2007-03-04
YESSS!!! :D 

Thanks heaps Bapoumba! You've saved my life!

Kia ora,
Gerald

---

