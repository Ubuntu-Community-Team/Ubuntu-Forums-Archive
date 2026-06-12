---
title: "quick question on adding lines..."
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-03-20
I have a 600e and need to "blacklist" some items and "add lines" to /etc/modprobe.d/alsa-base but to tell you the truth I know this should be simple but do i just go to the last line and just type in the lines, or do i need to proceed it with a # sign... what is the procedure? thanks for the help!

---

### Post by mlind on 2006-03-20
nano editor is very simple and easy to use, try with that
```
sudo nano /etc/modprobe.d/alsa-base
```

lines beginning with # are comments, so those are ignored.

---

### Post by IYY on 2006-03-20
I've never heard the term "black list" used in this context, but I'm pretty sure that you just want to comment the lines out by adding a # in the beginning. To add lines, just add them at the end of the file.

For example, if we have a file that looks like:

```

line 1
line 2 
line 3

```

When we "black list" line 1 and add line 4, it would look like

```

#line1
line2
line3
line4

```

---

