---
title: "ndiswrapper missing"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by killzoneman0 on 2006-06-16
does ndiswrapper come with the ubuntu iso, or do you have to download it separate.  i am missing mine along with a few other modules. should i reinstall?

---

### Post by Jagot on 2006-06-16
You could just download from the repos:

```
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by killzoneman0 on 2006-06-16
i am not currently connected to the internet on the ubuntu system. how would i go about getting on the internet with ubuntu after connecting the ethernet cord to the computer and modem?

---

### Post by az on 2006-06-16
ndiswrapper is there.  If you installed using the Desktop cd, boot into ubuntu and then put the cd into your drive.  The package manager will start and if you search for "ndiswrapper-utils" you will be able to install it - it is on the cd.

The kernel module is already part of the stock kernel that you are running.  The userspace tool is in the ndiswrapper-utils package.

Not everyone needs it, so it is not installed by default, but it is on the cd.

---

