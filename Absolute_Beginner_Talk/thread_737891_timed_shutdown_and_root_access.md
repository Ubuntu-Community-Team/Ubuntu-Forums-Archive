---
title: "timed shutdown and root access?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by djarcadian on 2008-03-28
So I want my computer to shutdown at midnight. When I use the shutdown -h 23:59 it says I need root access. I know nothing of root access. What can I do to make my computer shutdown automatically at midnight?

---

### Post by wormser on 2008-03-28
Put **sudo** before the command for root access.

```
sudo shutdown -h 23:59
```

---

### Post by kpkeerthi on 2008-03-28
See [Shutting Down From The Console Without A Password]("https://help.ubuntu.com/community/Sudoers#head-e8fcfa7c5e6475c732a518832babfe7d4f186ce3")

---

