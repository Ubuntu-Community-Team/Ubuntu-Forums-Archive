---
title: "Uninstall acer_acpi"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by jonttix on 2007-06-29
How do I uninstall acer_acpi? I have tried with sudo make uninstall but it wont work.

---

### Post by Pragmatist on 2007-06-30
If it doesn't come with an uninstall script, then you could always track down the files and remove them manually.  To use the locate command, do this:
```
sudo updatedb
```
This can take a few minutes to finish.  Then, you can search with keywords, for example:
```
locate acer
```
If you want to filter the results, use grep:
```
locate acer |grep acpi
```

---

### Post by jonttix on 2007-07-01
how do I then uninstall the files?

---

### Post by Pragmatist on 2007-07-01
You use the rm command (carefully!).  Read about the rm command:
```
man rm
```

---

### Post by jonttix on 2007-07-01
Ok Thanks!!

---

