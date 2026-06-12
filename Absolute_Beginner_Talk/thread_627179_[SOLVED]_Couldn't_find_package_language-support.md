---
title: "[SOLVED] Couldn't find package language-support ???"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by brugui00 on 2007-11-29
I'm trying to change the language, but when I try to change it inserting the code  ```
sudo apt-get install language-support-ca
``` i get the following error responce ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-support-ca
```

What can I do?? Did I mess up the installation??

Thanks

---

### Post by wormser on 2007-11-29
Have you opened up the Universe and Multiverse repositories?  System> Administration> Software Sources.

Another thing to do is update apt-get.

```
sudo apt-get update
```

---

