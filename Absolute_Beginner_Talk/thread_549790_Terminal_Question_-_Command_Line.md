---
title: "Terminal Question - Command Line"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by jso2897 on 2007-09-13
When navigating in the terminal, how do I indicate spaces in file names? In Wine applications, sometimes the Windows files have spaces in them. There maust be a way to get terminal to interpret a space correctly.:confused:

---

### Post by finer recliner on 2007-09-13
you must "escape" spaces in file/directory names. this can be done by placing a forward slash (\) in front of said space or wraping the entire path in quotes

```

$ cd /path/file\ with\ spaces
$ cd "/path/file with spaces"

```

---

