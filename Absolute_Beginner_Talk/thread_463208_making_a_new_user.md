---
title: "making a new user"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by moooody on 2007-06-03
How can I make a new user that have all the privilages of the user I created when installing ubuntu?

---

### Post by BatteryCell on 2007-06-03
```

useradd -m -s /bin/bash -G admin username

```

I believe would work.  If by same privileges you mean root like abilities. (you would still have to set their password though).

---

### Post by zvacet on 2007-06-03
```
sudo adduser username admin
```

---

### Post by zvacet on 2007-06-03
```
sudo adduser username
```

```
sudo adduser username admin
```

---

