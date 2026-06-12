---
title: "How do I execute a command in the to-be launched console?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-07-06
There are some applications that runs in the console, but I do not want to use the currently console.  So I would like to launch a new console and execute the application from there.

How would I in a single command launch a new console and excute an application?  Say I want to open a new console, and the console would start with nano opened.

I tried 'xterm && nano' and 'xterm | nano' but neither worked.

---

### Post by mali2297 on 2007-07-06
Try
```

xterm -e nano

```

---

### Post by kwacka on 2007-07-06
```

xterm -e nano &

```

hands the original console back for re-use

---

