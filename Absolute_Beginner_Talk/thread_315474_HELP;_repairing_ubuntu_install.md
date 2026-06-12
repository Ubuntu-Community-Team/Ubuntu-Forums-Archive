---
title: "HELP; repairing ubuntu install"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by PatsM on 2006-12-09
I followed steps described in "ATI/AMD fglrx in Ubuntu Edgy, step by step". Now I can't startup ubuntu anymore.
At startup i keep getting /bin/sh not found.
HELP; i don't wont to reinstall ubuntu from scratch (again).

---

### Post by taurus on 2006-12-09
Did you happen to change or modify /bin/sh by any change???    Which release are you running right now?

---

### Post by PatsM on 2006-12-09
I am running Edgy (6.10) and yes, it is possible i changed sh by following the guidelines in the hwo to :(

---

### Post by taurus on 2006-12-09
Boot your machine with the LiveCD, mount your partition where / is (probably /dev/hda1 but you need to check with your harddrive), and show me what does /bin/sh look like!

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
ls -la /mnt/ubuntu/bin/sh /mnt/ubuntu/bin/dash /mnt/ubuntu/bin/bash
```

---

