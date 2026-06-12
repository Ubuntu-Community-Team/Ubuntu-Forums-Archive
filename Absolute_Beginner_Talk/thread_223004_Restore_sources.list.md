---
title: "Restore sources.list"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by neal_nak on 2006-07-25
Not sure just what happened but I lost my sources.list. I see there are backup copies. How do I go about restoring the most recent copy?

Thank you,
Neal

---

### Post by The Seeker on 2006-07-25
```
sudo gedit /etc/apt/name_of_backup
```

Once it's open simply save as sources.list.

---

### Post by ubuntuuser on 2006-07-25
```
sudo cp /path/to/backup /etc/apt/sources.list
```

---

### Post by neal_nak on 2006-07-25
> **The Seeker said:**
> ```
sudo gedit /etc/apt/name_of_backup
```

Once it's open simply save as sources.list.


I am missing something. It tells me "You do not have the permissions necessary to save the file". I have created a Root password and logged in but still do not have permission.

---

### Post by neal_nak on 2006-07-25
got it. Thank you for the suggestions.

---

