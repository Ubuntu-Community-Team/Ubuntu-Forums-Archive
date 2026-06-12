---
title: "make command not working?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by devious on 2006-09-02
hi, i am unablt to get make to work. i used to use redhat a few years back and it seemed to just in in as standard. now when i try and run amke i get this...

```
make
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

```

it says 386 but i run a 686 and have /lib/modules/2.4.27-2-686 as well as 2.6.15-26-386 and 2.6.15.23-386 but only a build folder in the 686 dir and not in the other..

Any help woudl b appreciated :)

thanks

Alex

---

### Post by %hMa@?b&lt;C on 2006-09-02
```
sudo aptitude install build-essential
```

---

### Post by devious on 2006-09-02
sorry for wasting time ;) done ti :D

---

