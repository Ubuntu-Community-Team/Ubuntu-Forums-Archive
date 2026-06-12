---
title: "bash needed to execute command?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by galderz on 2005-12-18
just installed firefox 1.5, but when i try executing the 'firefox' command, it keeps coming back saying command not found. It's only when i execute:

bash firefox

that firefox actually runs, 

why is this?

---

### Post by endersshadow on 2005-12-18
Run this command in terminal:

```
sudo find /usr/bin -name 'firefox'
```

Let me know what you get as a result.

By the way, did you follow the wiki instructions for installing 1.5?

---

### Post by galderz on 2005-12-18
firefox is being found:

/usr/bin/firefox

I did follow the instructions in the how to. Could it be that the ln in the usr/bin is not correct?

---

### Post by galderz on 2005-12-18
i have firefox installed in /opt/firefox and i have just checked the link in the usr/bin directory and it's showing this:

lrwxrwxrwx  1 root root 13 2005-12-18 00:31 firefox -> /opt/firefox/

---

### Post by cwaldbieser on 2005-12-18
[QUOTE=galderz]just installed firefox 1.5, but when i try executing the 'firefox' command, it keeps coming back saying command not found. It's only when i execute:

bash firefox

that firefox actually runs, 

why is this?[/QUOTE]
How are you executing the (non-working) command?  Is it from a bash prompt, or some other shell, or something else?

---

### Post by galderz on 2005-12-18
obviously it was my fault. I had created the symbolic link to the directory instead of the actual executable.

sorry :-$

---

