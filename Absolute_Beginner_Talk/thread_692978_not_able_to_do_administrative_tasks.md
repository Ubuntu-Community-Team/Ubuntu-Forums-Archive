---
title: "not able to do administrative tasks"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by ejoftiduttu on 2008-02-10
While installation i made the administrative account dinesh. N accidently i did something on the account n i'm now unable to do an administartive tasks..How could i create a new account..

---

### Post by taurus on 2008-02-10
You do not need to create a new account (and it won't have root privilege anyway).  All you need to do is to add your login name back to group admin again if you want to have root privilege.

Boot into recovery mode from GRUB menu and run

```
useradd admin dinesh
shutdown -r now
```

---

