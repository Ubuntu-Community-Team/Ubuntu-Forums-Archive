---
title: "Synaptic uninstalled"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by DaemonLee on 2006-06-20
How do you reinstall Synaptic if you've uninstalled it? 


I've tried; 

```


steven@TuxVII:~$ sudo apt-get install synaptic
Password:
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate

```

Any assistance?

By the way, I uninstalled Synaptic due to the fact that after it did it's redundancy test or whatever, it would just close. All on it's own into the background and not function. The package manager would still work, though.

---

### Post by aysiu on 2006-06-20
Get a fresh sources.list
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then ```
sudo aptitude update
sudo aptitude install synaptic
```

---

### Post by DaemonLee on 2006-06-20
Hey, can someone tell me what applications are uinstalled with Synaptic when you try to uninstall Synaptic? 

Since, stupid me, forgot to write them down. Thanks.

---

