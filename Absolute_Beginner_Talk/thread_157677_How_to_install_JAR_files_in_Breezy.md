---
title: "How to install JAR files in Breezy?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by nala on 2006-04-09
How do I install a JAR file? I tried clicking "extract" but it didn't seem to work. I'm using  Sun's latest Java release.

---

### Post by xXx 0wn3d xXx on 2006-04-09
[QUOTE=nala]How do I install a JAR file? I tried clicking "extract" but it didn't seem to work. I'm using  Sun's latest Java release.[/QUOTE]
What are you trying to install ??? Try looking in the repositories or see if they have a .deb, .rpm, or .tar.gz file on the site.

---

### Post by Qrk on 2006-04-09
You can run them using the command line. First make sure the file is executable (right click on it in nautilus and select -Preferences->Permissions)

You can run it in a terminal by writing:

```
java -jar /path/to/file.jar
```

---

