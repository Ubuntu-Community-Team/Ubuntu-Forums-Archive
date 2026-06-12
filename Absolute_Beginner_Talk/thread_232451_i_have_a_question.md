---
title: "i have a question"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by bkizzle on 2006-08-08
I am trying to update from hoary and am running into some problems. I ran update and everything but when i go to run sudo apt-get upgrade or dist-upgrade, it says segmentation faulty tree 0%. can anyone tell me what im doing wrong here.

---

### Post by Jagot on 2006-08-08
Are you trying to update to Breezy?  If you're trying to upgrade directly to Dapper it can't be done (or at least not without errors).

---

### Post by SickTwist on 2007-05-04
I just encountered the same problem and found a fix [here]("http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/").

To fix it, open a terminal and run the following comands:

```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
```

Hopefully that takes care of your problem.

---

