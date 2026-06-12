---
title: "Permission denied???"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by digags on 2007-08-29
I want to download updates from a local mirror...........for which I was trying to modify 

**nano /etc/apt/sources.list**

but when I try saving the changes it shows an error saying permission denied...

what should I do??

---

### Post by Kobalt on 2007-08-29
```
sudo nano /etc/apt/sources.list
```
You should read this about [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Marat Galiev on 2007-08-29
use sudo command.
like this
sudo nano /etc/atp/sources.list
enter you password.

---

