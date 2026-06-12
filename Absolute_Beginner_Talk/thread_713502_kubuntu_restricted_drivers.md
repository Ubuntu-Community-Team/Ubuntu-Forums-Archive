---
title: "kubuntu restricted drivers"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by padamon on 2008-03-02
Today I installed kubuntu amd64 gutsy from a cd

When I try to get into restricted driver manager it says:
"You need to install the package  linux-restricted-modules-2.6.22-14-generic  for this program to work."

I go sudo apt-get install linux-restricted-modules-2.6.22-14-generic
and I get
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " 

I type alt-f2 and write the dpkg --configure -a.
It appears to do nothing and same thing when I try the command again


Also, when I run adept manager it tells me 
"Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself."


Thanks in advance for any help. I've gotten a headache googling for the last couple of hours and I really need my wireless.

---

### Post by overdrank on 2008-03-02
HI and you will need to run that command in the terminal
```
sudo dpkg --configure -a
```

---

