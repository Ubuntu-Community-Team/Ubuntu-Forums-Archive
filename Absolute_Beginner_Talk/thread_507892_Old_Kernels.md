---
title: "Old Kernels"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by fattom23 on 2007-07-23
Is there any particular reason that I have to use the newest kernel available?  I was a Dapper user and I recently updated to Feisty.  This, of course, updated the kernel to the newest generic kernel available.  Ever since, I've been having serious stability issues (random freezes which necessitate restarting X, etc).  When I boot into the latest 386 kernel, I don't have the freezing issue. I want to roll back to the 686 kernel, which was working just fine for me, and supported my dual core processor.  Should this cause me any issues?  Thanks a lot, and sorry for the lack of precision in this post (I'm fairly new to Linux, and don't always know a lot about the way it works).  Anyway, thanks a lot for any advice you can provide.

---

### Post by ddrichardson on 2007-07-23
> **fattom23 said:**
> Is there any particular reason that I have to use the newest kernel available?  I was a Dapper user and I recently updated to Feisty.  This, of course, updated the kernel to the newest generic kernel available.  Ever since, I've been having serious stability issues (random freezes which necessitate restarting X, etc).  When I boot into the latest 386 kernel, I don't have the freezing issue. I want to roll back to the 686 kernel, which was working just fine for me, and supported my dual core processor.  Should this cause me any issues?  Thanks a lot, and sorry for the lack of precision in this post (I'm fairly new to Linux, and don't always know a lot about the way it works).  Anyway, thanks a lot for any advice you can provide.

No, if the previous kernel worked keep it. The philosophy is that instead of hunting down new individual drivers, the latest set of drivers is installed for all devices. The problem, as you've discovered is that, like WIndows you can still have a rogue driver.

There may be some packages dependent on the latest kernel, but this is unlikely.

---

