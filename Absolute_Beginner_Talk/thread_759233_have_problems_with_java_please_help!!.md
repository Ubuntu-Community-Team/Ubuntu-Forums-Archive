---
title: "have problems with java please help!!"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by darketo on 2008-04-18
i was installing a program and it tells me that some dipendencies are not suitable it is jre i dont really remember de version it is asking me for but i have Ubuntu 6.06 whatever info will be aprecieated


greetings

---

### Post by Triggerhapp on 2008-04-18
[www.java.com](www.java.com)

There may also be packages in the restricted repositories... either way works

---

### Post by 3rdalbum on 2008-04-18
Are you trying to install a program from outside the repositories? (i.e. one that you've downloaded from a website, or that you got off a Linux magazine CD?)

Ubuntu 6.06 is very old, so it has an earlier version of Java. The easiest (and most fulfilling) way of getting the latest version of Java is to upgrade to the latest version of Ubuntu.

---

### Post by zvacet on 2008-04-19
Look in synaptic for sun-java6-bin and if you have it install it.After that type in terminal 

```
sudo update-alternatives --config java
```

and choose sun-java6

---

