---
title: "Wrong Keyboard hampers logon"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Roland'S on 2008-01-03
I installed Ubuntu Feisty using Wubi. My physical keyboard is US International. However, upon logon, laptop thinks it is UK. Hence errors in password. After logon, I can adapt keyboard setting, using System>Preferences>Keyboard. Alas, laptop forgets this after logoff. Hence problem persists. Where in the system should I make an adaptation?

Thanks for advice!!

---

### Post by forestpixie on 2008-01-03
I think you can reconfigure the keyboard by using

```
sudo dpkg-reconfigure xserver-xorg
```

wait for someone elseto confirm or have a better idea

---

