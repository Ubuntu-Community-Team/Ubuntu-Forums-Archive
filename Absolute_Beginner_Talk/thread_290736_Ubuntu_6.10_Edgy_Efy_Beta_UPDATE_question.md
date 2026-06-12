---
title: "Ubuntu 6.10 Edgy Efy Beta UPDATE question"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by drx0 on 2006-11-01
Do the automatic updates in the Ubuntu 6.10 Edgy Efy Beta UPDATE you to the final release?  If not, what do you have to do to get there?

Thank you!

---

### Post by pbaehr on 2006-11-01
I can't speak for Edgy since this time I waited until the final release, but that's how it worked in Dapper.

So if it's the same and your system is fully updated, you should have the final release. (Providing it is the same as it was for Dapper)

---

### Post by bvucinic on 2006-11-01
Yes, nothing special to do.

---

### Post by nyinge on 2006-11-01
In Dapper, I just had to replace the words "Dapper" with "Edgy" in sources.list and do the "apt-get dist-upgrade".  So, I'm assuming it would update the necessary packages automatically in your case, though I cannot be 100% sure.

---

### Post by pbaehr on 2006-11-01
> **nyinge said:**
> In Dapper, I just had to replace the words "Dapper" with "Edgy" in sources.list and do the "apt-get dist-upgrade".  So, I'm assuming it would update the necessary packages automatically in your case, though I cannot be 100% sure.

That's if you are upgrading from one release to the next one. In this case, the OP is already running Edgy so his sources should already be for Edgy.

---

### Post by PriceChild on 2006-11-01
```
sudo apt-get update
sudo apt-get dist-upgrade
```Will ensure you're running final :)

---

