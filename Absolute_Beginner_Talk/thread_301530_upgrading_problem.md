---
title: "upgrading problem"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-11-17
Hello,

I want to upgrade my ubuntu 5.10 to 6.06, but I get these two errors:

> Failed to fetch cdrom:[Ubuntu 5.10 _breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


Could you say me what this means and what I can do?

Thanks,

---

### Post by Bachstelze on 2006-11-17
About time you upgrade ;)

open your sources.list

```
sudo nano /etc/apt/sources.list
```

and delete every line mentioning the cdrom. Then save your file (Ctrl+O, Return to confirm) and exit nano (Ctrl+X). Then run apt-get update again.

---

### Post by linux-beginner on 2006-11-17
Thanks HymnToLife!

---

