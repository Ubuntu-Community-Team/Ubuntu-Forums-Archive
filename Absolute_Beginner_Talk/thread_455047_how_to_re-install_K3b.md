---
title: "how to re-install K3b"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-05-26
I have inadvertently permanently removed k3b from the repositories and need to get it back. Could someone please explain how ? Is it achievable from the /var/cache/apt/archives ?

---

### Post by meborc on 2007-05-26
to install k3b open terminal and do```
sudo apt-get install k3b
```

---

### Post by linuxnooby on 2007-05-26
But if it's not in the repository, that won't work

---

### Post by linuxnooby on 2007-05-26
Sorry - Forget my previous post. It does work

---

### Post by pbw on 2007-05-26
ls /var/cache/apt/archives/ | grep k3b

then sudo dpkg -i *k3b deb*

Though i dont understand the prob, that's how you can reinstall the cached archive.

-- pbw

---

