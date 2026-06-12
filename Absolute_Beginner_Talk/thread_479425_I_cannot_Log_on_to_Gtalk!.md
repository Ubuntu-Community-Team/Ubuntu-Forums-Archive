---
title: "I cannot Log on to Gtalk!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-06-20
Hello, everyone. Whenever I try to log on to my Gtalk account, it throws this error:

> SSL support could not be initialized for account ********@gmail.com. This is most likely because the QCA TLS plugin is not installed on your system.

It says this is a plugin, but I'm not sure which one. I tried searching for it, no luck. If anyone knows, please tell me! :(

---

### Post by yagood on 2007-06-20
Open Synaptic and search for "qca-tls" and install it.

Or simply type in the console:

```
sudo apt-get install qca-tls
```

---

