---
title: "nautilus only boots prtitions only if not on /etc/fstab!"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-04-04
If I put, in /etc/fstab, a line like this
```

/dev/sdb1 /media/WinVista ntfs rw,auto,user,exec

```

Then, I can mount /dev/sdb1 normally by using mount and umount, but I can't mount it on nautilus. However, it I remove the line, I can mount it on nautilus but not on mount. Any answer?

---

### Post by Fixman on 2008-04-05
No answer?

---

### Post by Fixman on 2008-04-05
Please help!

---

### Post by Fixman on 2008-04-05
Oh, come on!

---

### Post by Fixman on 2008-04-05
Please! Im suffering!

---

### Post by joshrobinson on 2008-04-05
what if you try... this line

```
/dev/sdb1 /media/WinVista ntfs defaults,umask=0000 0 0
```

---

### Post by Fixman on 2008-04-05
> **joshrobinson said:**
> what if you try... this line

```
/dev/sdb1 /media/WinVista ntfs defaults,umask=0000 0 0
```

Same effect.

---

### Post by joshrobinson on 2008-04-05
> **Fixman said:**
> Same effect.

did your reboot to see if it mounts automatically? if not you can try the ntfs-3g approach

---

