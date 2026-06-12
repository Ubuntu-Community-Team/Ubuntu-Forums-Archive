---
title: "ls after cd"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by netimen on 2007-10-04
can I make 'ls' command run automatically after 'cd' command?

---

### Post by rsambuca on 2007-10-04
```
cd /new/folder && ls
```

---

### Post by bodhi.zazen on 2007-10-04
cd /new/directory; ls

---

### Post by netimen on 2007-10-04
Oh, thank you, but can I have 'cd /new/folder' and then ls automatically somehow?

---

### Post by mdebusk on 2007-10-04
> **netimen said:**
> can I make 'ls' command run automatically after 'cd' command?

In .bashrc, place the following shell function:
```

lcd() { cd ${1} ; ls ; }

```

When you start a new shell, you can type "lcd" and the directory you want, and this should give you the result for which you're asking.

---

### Post by netimen on 2007-10-04
Thank you mdebusk - this is exactly what I needed

---

### Post by mdebusk on 2007-10-05
> **netimen said:**
> Thank you mdebusk - this is exactly what I needed

You're welcome.

In case you're wondering why a shell script or alias wouldn't do, it's because they spawn a separate instance of the shell. So you'd get the directory listing you wanted, but you'd end up in the directory you thought you left. The function I offered uses the current instance.

Make sure to mark the thread "solved". :)

---

