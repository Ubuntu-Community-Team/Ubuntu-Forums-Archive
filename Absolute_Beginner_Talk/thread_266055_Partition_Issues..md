---
title: "Partition Issues."
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by DaemonLee on 2006-09-26
I had a spare partition made in the parition manager.

My issue, is that it claims that only root has access to it.

What the CHMOD command to alter this to allow the username 'steven' to have access to it?

---

### Post by pistcivet on 2006-09-26
Personally, I prefer to take ownership:
sudo chown steven:steven /path/to/mounted/volume

Another possibility:
sudo chmod 777 /path/to/...
(but that gives everyone read/write/execute permissions.)

---

### Post by DaemonLee on 2006-09-26
It works! It works! :-D

---

