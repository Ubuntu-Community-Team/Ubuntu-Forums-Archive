---
title: "Adept Manager update issues"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by mastergunner on 2007-12-20
Guys I have just put Kubuntu Gutsy 7.10 on my computer. The notifier comes on and says I have a bunch of updates. When I start updating adept never completes. Is there a a command that looks something like below that will complete the updating and configure them?

sudo apt ### && sudo apt ##

---

### Post by PmDematagoda on 2007-12-20
I think what you want is:-

```
sudo dpkg --configure -a
```

---

