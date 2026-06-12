---
title: "Deleting Something From Root In KDE"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-10-04
Hi, I made a backup (wrongly) of my computer and need to delete the file, i'm in KDE and when I open it in Konqueror and move to trash, it moves it to root trash rather than user trash (if that makes sense) so I can't delete it. Is there a way I can do this without allowing login as root and deleting it that way, at the moment the file is in root trash at:

/root/.local/share/Trash/files/backup_4.tgz

Any help appreciated

Calv

---

### Post by konst88 on 2006-10-04
sudo rm /root/.local/share/Trash/files/backup_4.tgz

---

### Post by Ben Sprinkle on 2006-10-04
```

su
rm '/root/.local/share/Trash/files/backup_4.tgz'

```
:)

---

### Post by calvinthomas on 2006-10-04
Thankyou people, that worked great! I tried sudo rem and sudo remove! Need to remember sudo rm

Calv

---

