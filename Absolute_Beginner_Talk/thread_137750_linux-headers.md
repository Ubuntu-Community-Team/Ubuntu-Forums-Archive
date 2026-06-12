---
title: "linux-headers"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-02-28
where do i get the latest header files...i'm trying to install a vpnclient but don't seem to be successful..i think the header fiels are the issue. I have been told to get them by people on here..but where do i look?

---

### Post by kaamos on 2006-02-28
You can install them from synaptic. I'd have to know your kernel version to give you the name of the right package, but you can use this command to install them as well.

Open Applications->Accessories->Terminal and type:
```
sudo apt-get install linux-headers-$(uname -r)
```

---

