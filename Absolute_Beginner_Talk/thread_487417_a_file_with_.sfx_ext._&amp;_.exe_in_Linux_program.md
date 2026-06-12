---
title: "a file with .sfx ext. &amp; .exe in Linux program"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-06-29
I have a program where two files must be used for installation one setup.sfx and the instruction says -- be sure setup.sfx has executable flag (chmod +x )-- how to do that the other file is keymaker.exe how someone help me install it.

---

### Post by mali2297 on 2007-06-29
Are those files really for Linux? By the extensions to their names, they appear to be Windows executable and will not run in Linux.

However, if they are for Linux, type the following in the terminal:
```

chmod +x setup.sfx keymaker.exe

```

---

### Post by cogadh on 2007-06-29
sfx is a self-extracting archive in a Windows executable format similar to exe. Neither of those files will work natively in Linux. You could try running them with Wine, though.

---

