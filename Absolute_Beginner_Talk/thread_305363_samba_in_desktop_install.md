---
title: "samba in desktop install"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2006-11-23
Hi, 

I was wondering if the samba server was present in the desktop 6.10 install package. I was wanting to set up samba but the start/stop scripts are not present. Shoud i download the server version?

cheers

c.

---

### Post by taurus on 2006-11-23
No need to install a server version.  If samba is not on your system, use synaptic/apt-get/aptitude to install it...  And whatever else you need, just install it.

```
sudo aptitude update
sudo aptitude install samba
```

---

