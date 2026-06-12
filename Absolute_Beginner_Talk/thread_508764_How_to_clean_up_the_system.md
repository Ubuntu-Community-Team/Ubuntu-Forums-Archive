---
title: "How to clean up the system?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by crazydude2007 on 2007-07-24
I installed many different utilities, and I now want to clean up all my temporary files, and files that I do not need any longer. For example in Windows, there is "Disk Cleanup", what is it like in Ubuntu? I am very new, sorry for a newb question ^_^ . Thanks in advance

---

### Post by ubuntu.daemon on 2007-07-24
```
user@home: sudo apt-get clean
user@home: sudo apt-get autoclean
user@home: sudo apt-get autoremove
```

think that will get all your temporary files....

---

