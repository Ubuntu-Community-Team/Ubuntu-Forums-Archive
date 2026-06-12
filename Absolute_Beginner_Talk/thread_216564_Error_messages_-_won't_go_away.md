---
title: "Error messages - won't go away"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by masonj7 on 2006-07-15
E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

i get these errors after installing any programs.  i used the add/remove programs to add all available programs while i have an internet connection.  after i did that is when these errors showed up.  now anytime i install anything using synaptic i get them.

any ideas?

---

### Post by Swab on 2006-07-15
You installed everything? Wow!  Anyway I'm pretty sure you don't need those 3 packages.  Try opening a terminal and typing..

```
sudo apt-get remove clvm redhat-cluster-suite system-config-cluster
```

then enter your password.

---

### Post by masonj7 on 2006-07-17
thanks for the code.  i think it worked, but there was an error at the end.  i think it was b/c i was not connected to the internet at the time.  i will try to verify that when i am connected.

still working on the wireless card issue.

---

