---
title: "network drive in a windows pc"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by mayday56 on 2007-04-23
is there a way to mount a windows network drive thats in another pc on my home network?

---

### Post by Cypher on 2007-04-23
Absolutely..
```

sudo apt-get install smbfs

```
Then
```

sudo mkdir /mnt/WinDir

```
Then
```

sudo mount -t smbfs -o username=<windows user>,password=<windows password> /<Windows PC IP>/path/to/directory /mnt/WinDir

```

Regards

---

### Post by mayday56 on 2007-04-23
thanx for the response but Im a newbie and im having a heck of a time with that last command line......could you explain so a complete idiot(me) can get it right? thanx

---

