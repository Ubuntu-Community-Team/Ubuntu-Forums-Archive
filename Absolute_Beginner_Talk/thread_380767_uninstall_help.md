---
title: "uninstall help"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by michie86 on 2007-03-10
Hi,

How do I uninstall something that I installed using './configure' and 'make install'?

Thanks

---

### Post by taurus on 2007-03-10
In the same directory that you ran those three commands (./configure, make, sudo make install), you would run

```
sudo make uninstall
```

---

### Post by michie86 on 2007-03-10
thanks but when I do it I get

no rule to make 'uninstall'

---

### Post by ShackledMystic on 2007-03-10
in order to make " sudo make uninstall " work :

1. You shouldve installed the package successfully.
2. You should be in the directory where the package files were extracted [source package]


when these two conditions are met -- uninstall SHOULD work 


see if u have both these things done properly 


PEACE

---

### Post by michie86 on 2007-03-10
I am in the right directory, and I think I installed it successfully, well, 'I think'..

oh my

---

