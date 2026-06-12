---
title: "latest kernel?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-28
Is dapper drake 6.06 currently using the latest linux kernel?

I ask because i'm trying my darndest to get SLI working but according to nvidias guide, my system isnt registering the devices on the proper bridge device and they say the only way to fix it is to upgrade the kernel....

thanks in advance

---

### Post by R3linquish3r on 2006-05-28
Dapper is currently using the 2.6.15 kernel. The latest is 2.6.16. Both compiling a new kernel and upgrading to Dapper can be a bit tricky. Dapper seems stable enough to me though that you could take that route.

I had the most success with this method:

```
gksudo "update-manager -d"
```

---

