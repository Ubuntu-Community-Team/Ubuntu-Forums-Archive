---
title: "ExternalHard drive"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by ericunicast on 2006-09-23
i need to take ownership of an external hard drive so i can use it. how do i do it? running breezy badger.h

---

### Post by benuski on 2006-09-23
Try typing this into the terminal:

```
sudo chown -R ${USER}:${USER} /media/sda1
```

You may need to replace /media/sda1 with the path that your external drive is at, but that is the default.

---

### Post by ericunicast on 2006-09-23
that didnt work

---

### Post by benuski on 2006-09-23
hmm..

Try this instead

```
sudo chown -R ${USER}:${USER} /dev/sda1
```

If that doesn't work, I`ll have to try and think up a whole new strategy...

---

### Post by dbd on 2006-09-23
What exactly is the problem? Is the drive mounted? Can you read the hard drive, but just not write to it? Does it use the NTFS filesystem (if you don't know what this means then was it used in windows, and if so then which version of windows)?

---

