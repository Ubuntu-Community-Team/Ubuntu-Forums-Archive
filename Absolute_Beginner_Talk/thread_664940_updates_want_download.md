---
title: "updates want download"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by jaguar_jax on 2008-01-11
When I click the icon for updates when it's lit, the system tells me this command?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Please help me with this problem.

---

### Post by taurus on 2008-01-11
Close the update window first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dcstar on 2008-01-11
> **jaguar_jax said:**
> When I click the icon for updates when it's lit, the system tells me this command?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Please help me with this problem.

Open a terminal, then:
```
sudo dpkg --configure -a
```

---

