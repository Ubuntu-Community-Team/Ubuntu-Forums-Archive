---
title: "update glitch"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by berninghausen on 2008-02-26
The little orange icon says there are updates to Gutsy Gibbon.  Attempting to install them results in a message that dpkg needs to be configured.  

Trying to plug the exact command into Terminal--'dpkg --configure -a'--scolds me and says I need superuser privilege.

What is superuser privilege and why isn't it defined in the GG documentation?

:confused:

---

### Post by SOULRiDER on 2008-02-26
Open a terminal and do:
```
sudo dpkg --configure -a
```

Superuser privileges means you have to be root. On Ubuntu you cannot use the root account, but you can use the sudo command to temporarily obtain superuser privileges. Also, note that when its asking for your password and you type you wont see any *'s but it is indeed typing.

---

### Post by berninghausen on 2008-06-22
Belated thanks.  Moving on to Heron, but if I can't find a way to install Kmymoney0.9, I'll keep trying other distributions.  There will be another posted plea soon!

---

