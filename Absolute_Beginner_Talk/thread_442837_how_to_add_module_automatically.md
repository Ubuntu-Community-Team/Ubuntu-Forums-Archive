---
title: "how to add module automatically?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by wildseven on 2007-05-13
hello.
to use my wired connection i have to modprobe e100.
when i restart it goes away and i have to add it again.
how can i have it so i just type it once and it will load the module automatically if i restart?

-seven

---

### Post by Acksys on 2007-05-13
Add it to /etc/modules

---

### Post by Bachstelze on 2007-05-13
For a "one-liner" :

```
echo "e100" | sudo tee -a /etc/modules
```

---

