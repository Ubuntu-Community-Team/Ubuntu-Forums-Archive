---
title: "Synaptic Repositories"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-12
Is there to see repositories i can add to synaptic to get more software chooses?

---

### Post by por100pre1 on 2007-10-12
Yes, however, it can become troublesome when upgrading or updating your system. The Canonical commercial repository only has a few programs but it is very safe for your system:

```
sudo su -c 'echo deb http://archive.canonical.com/ubuntu feisty-commercial main >> /etc/apt/sources.list'
```

The [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository is good too. There are many some pieces of software there that you won't see in the Ubuntu repositories.

Be sure to disable these repositories when upgrading to Gutsy.

---

