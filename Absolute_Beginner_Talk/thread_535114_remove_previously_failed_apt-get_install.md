---
title: "remove previously failed apt-get install"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-08-26
I tried to install sun-java6-doc along with the others sun-java6-xxx but it seems that the -doc is not available so the installation failed.

I do not longer care for it, but since then every time I install something with sudo apt-get install I get the warning that that package is not available and it gives me the option of abort or retry.

how can I tell apt-get to stop trying to install that package?

---

### Post by bme on 2007-08-26
try "sudo apt-get install -f"

---

### Post by jdrodrig on 2007-08-26
thanks for the reply, but no luck...even after trying that...the next time I installed something, I got the same message...any other ideas?

---

