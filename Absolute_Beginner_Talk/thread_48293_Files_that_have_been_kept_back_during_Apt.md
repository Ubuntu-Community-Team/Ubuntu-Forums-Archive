---
title: "Files that have been kept back during Apt"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by NateC on 2005-07-11
I have many files that have been kept back while trying to update Ubuntu. Is there a command which will install them all... example:

$ sudo apt-get upgrade keptbackfiles

---

### Post by Xian on 2005-07-11
No, but you do need to find out the reason they are being held back.
The way to do this is to instruct apt to install those packages specifically.

It will then give you a detailed message (if needed) of why they are blocked.

```
$ sudo apt-get install keptback_packagename
```

---

