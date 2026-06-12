---
title: "problem with wine"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by kensou on 2007-05-11
i have installed wine but i when i try to open a exe with it it gives the error
wine: could not load L"c:\\windows\\system32\\ng.exe": Module not found
 somebody please help me

---

### Post by Praill on 2007-05-11
Im assuming the phantom windows drive is already set up. But just in case run the initial config so wine can create it :
```

winecfg

```

This is generally the message you get when the file in question simply does not exist.
The phantom drive it will create will be in /home/<user>/.wine/drive_c (replace <user> with the current user) so check in there to make sure the file actually exists.

Sorry if this is all too obvious and no help.

---

