---
title: "command line cd burning"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by katiad on 2005-10-19
Hi! So... I attempted to upgrade to Breezy, and everything went all wrong. X is dead, the locales are messed up, and amidst it all, I discovered that my /home/ partition isn't really a partition. So... since I don't have much on there yet, and I'm willing to do a complete reinstall to fix the partition problem, I'd like to do that. Unfortunately, I do have some things I'd like to back up... and I'm not sure how to back things up to a cd while using the command line only. 

I'd like to back up my /home/me folder and everything inside it. Shouldn't take more than 1 cd. Help, please? :)

---

### Post by aysiu on 2005-10-19
Do you have the Universe repositories enabled? If so ```
sudo apt-get install burn
``` I hope burn has a man page: ```
man burn
```

---

