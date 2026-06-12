---
title: "Internet connection ok but cant access repositories"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by carrizz on 2008-02-21
Hi, I have an active internet connection via an adsl ethernet modem. I can access the net using firefox but I cant connect to the repositories using synaptic. The update icon also times out.
Hope someone can help, thanks.

---

### Post by Crafty Kisses on 2008-02-21
> **carrizz said:**
> Hi, I have an active internet connection via an adsl ethernet modem. I can access the net using firefox but I cant connect to the repositories using synaptic. The update icon also times out.
Hope someone can help, thanks.

Have you tried getting any of the repositorys through the Terminal?

---

### Post by spiderbatdad on 2008-02-21
could you post the output you get when running ```
sudo apt-get update
```

---

### Post by seventhc on 2008-02-21
I'd also post the output of this.
```

cat /etc/apt/sources.list

```

---

