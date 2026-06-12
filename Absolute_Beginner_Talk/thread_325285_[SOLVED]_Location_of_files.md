---
title: "[SOLVED] Location of files"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-25
Would someone be so kind as to tell me _how_to find the Dell printer drivers in the file system. Then if not how maybe where they are kept. I have searched but search doesn't show a thing. I started to go through each directory but gave up. :)

Thanks and merry xmas

---

### Post by meng on 2006-12-25
Not sure, but if (from your earlier posts) you installed a deb file (converted from rpm), the way to uninstall that is to:
sudo dpkg -P (name of deb file)

---

### Post by squrl on 2006-12-25
I don't want to uninstall it. I need to get to it and do a little editing. Uninstalling the printer does not remove the driver. It is there to stay. I want to get my grubby hands on the elusive devil.

---

### Post by Regel on 2006-12-25
```
sudo updatedb
locate name_name_name
```

---

