---
title: "Compleste uninstall of programs"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-02-20
I have noticed that a lot of programs require some additional libraries to be installed on the system but then you reinstall the program the libraries stay. how do I remove libraries that are not use by any program and in fact how do I remove stuff that is not used by any program. My main concern now are the left over libraries.

---

### Post by jan quark on 2008-02-20
try to run in terminal

```
sudo apt-get autoremove
```

this should delete all not needed libs

---

### Post by Anicka on 2008-02-20
There is a program you can install from synaptic called gtkorphan. It shows packages that aren't depending on anything else in your system. It can be a useful tool for this type of problems, but beware, a lot of the packages listed as orphans are essential to your system (e.g. kernels).

---

