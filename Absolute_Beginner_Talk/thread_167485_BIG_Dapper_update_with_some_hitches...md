---
title: "BIG Dapper update with some hitches.."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Rinzwind on 2006-04-28
> W: Failed to fetch http:// au.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db-engine/foomatic-db-engine_3.0.2-20060318-1ubuntu1_i386.deb
  404 Not Found


W: Failed to fetch http:// au.archive.ubuntu.com/ubuntu/pool/main/d/discover1-data/discover1-data_1.2005.11.25ubuntu7_all.deb
  404 Not Found


Should I worry about these 2 messages?

---

### Post by pbaehr on 2006-04-28
It's probably a problem on their end, not yours. I'd wait a little while and then run:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by Rinzwind on 2006-04-28
Thank you :)

I was allready checking if it was a repo I didn't have :D :D

Hmm could I change the AU in the URL to US or so and try again? 
Cuz now get an annoying update ikon on my panel :D

---

### Post by pbaehr on 2006-04-28
If you didn't have the repository it wouldn't know to look there for updates. I suppose using the us address should work.

---

