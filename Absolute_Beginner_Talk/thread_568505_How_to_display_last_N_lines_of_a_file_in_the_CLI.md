---
title: "How to display last N lines of a file in the CLI?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Sporkman on 2007-10-05
Is there a command to display the last N lines of a text file in the CLI?

-Thx

---

### Post by HermanAB on 2007-10-05
tail -n 50 filename
head -n 50 filename

and for a running commentary:
tail -f /var/log/messages

Cheers,

Herman

---

### Post by Sporkman on 2007-10-05
Awesome, thanks! 8)

---

### Post by hardyn on 2007-10-05
cat <filename> | less

works nicely too.

---

