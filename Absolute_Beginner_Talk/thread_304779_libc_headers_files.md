---
title: "libc headers files"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by zemarques on 2006-11-22
I have just installed Ubuntu 6.10. When i try to install a nvidia driver it shows a message saying that i haven't "libc headers files". What does this means? How can i solve this?
:???:

---

### Post by Perfect Storm on 2006-11-22
Is it the nvidia driver from synaptic or from the nvidia page?

---

### Post by Bachstelze on 2006-11-22
To install the nvidia drivers from the installer provided by nvidia, you neet to install some stuff before, open a terminal and run this :

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by ybh6336 on 2007-06-29
Thanks a lot, that post helped me install Beryl on my Ubuntu.

Regards.

---

### Post by reaper_rr on 2008-04-28
> **HymnToLife said:**
> To install the nvidia drivers from the installer provided by nvidia, you neet to install some stuff before, open a terminal and run this :

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

I have the same problem but i cannot run 
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
properly.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential
```

---

