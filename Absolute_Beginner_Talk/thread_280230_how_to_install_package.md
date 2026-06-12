---
title: "how to install package?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by tiendn on 2006-10-19
I have installed Ubuntu, I see some package in var/cache/apt/archive ! Can I copy that packages to different computer( be installed Ubuntu) and install them on that computer?

---

### Post by elpuerco on 2006-10-19
If the other computers have Linux on them why not just install directly from a repository, .deb file etc?

---

### Post by Bachstelze on 2006-10-19
Hi and welcome to Ubuntu :)

Yes, you can, just run the following command on the second computer :

```
sudo dpkg -i filename.deb
```

Beware though, dependencies will *not* be managed, you'll have to install them all manually.

---

### Post by PriceChild on 2006-10-19
Yup :)

By putting them in /var/cache/apt/archive and using the apt-get command. (dependencies managed)

Or navigating to them in terminal and using:
```
sudo dpkg -i <<package name>>.deb
```

---

### Post by PriceChild on 2006-10-19
> **elpuerco said:**
> If the other computers have Linux on them why not just install directly from a repository, .deb file etc?Saves time, bandwidth and traffic.

---

### Post by tiendn on 2006-10-19
Thanks! I will try.

---

### Post by elpuerco on 2006-10-19
> **PriceChild said:**
> Saves time, bandwidth and traffic.

Duly noted ;)

---

