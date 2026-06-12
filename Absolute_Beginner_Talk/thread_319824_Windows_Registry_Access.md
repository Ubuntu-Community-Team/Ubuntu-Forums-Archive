---
title: "Windows Registry Access"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by nomy on 2006-12-16
Hello. To install Photoshop I need **HKEY_LOCAL_MACHINE/Software/Adobe/** . How can I access it to create adobe.reg for future use of wine? I know the location but how to open Software Registry file on Ubuntu?

---

### Post by ngch on 2006-12-16
I'm not very sure if this will work, but you can start the wine version of regedit using this command:

```
wine regedit
```

Try creating the key, and see if it works.

---

