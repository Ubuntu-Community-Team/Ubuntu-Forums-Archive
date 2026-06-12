---
title: "Server woes....."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Brow 71 on 2006-09-03
Just installed server edition. There does not seem to be a graphical desktop,only command prompts.What can I do to make it look like a more traditional interface?

---

### Post by Miademora on 2006-09-03
You can do something like:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Brow 71 on 2006-09-04
Thanks. I tried that solution and was met with  a message that it could not find that package.any ideas?

---

### Post by Bachstelze on 2006-09-04
```
wget http://fkraiem.free.fr/sources.list_dapper
sudo mv sources.list_dapper /etc/apt/sources.list
sudo apt-get update
sudo aptitude install ubuntu-desktop
```

---

