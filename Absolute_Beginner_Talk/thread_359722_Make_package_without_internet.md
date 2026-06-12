---
title: "Make package without internet"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by chrispy212 on 2007-02-12
I am using an old box for my Ubuntu needs. I don't have exact specs, but they arent important.
Anyway, I have had Ubuntu running on it before, but experienced kernel crashes after installing a bad driver with NDISwrapper. 
I feel that network is a neccesity for a linux box, and so I am attempting to get ndis working (again) so I can connect to my wireless network.

I cannot 'make' as I do not have the packages, and downloading them and their dependancies, and THEIR dependancies independatly takes a few weeks! and obviously I annot use APT (and wireless is my only option)
I am asking if there is any package that contains EVERYTHING I need to get make running on a fresh install. 
Thanks

---

### Post by taurus on 2007-02-12
Build-essential is on the install CD so insert it into a drive and type

```
sudo apt-cdrom add 
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by chrispy212 on 2007-02-12
Thank you very much!
I think I can use package manager in gnome as well then...
Again, thanks!

---

