---
title: "How do I remove all but two TTY?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-11-11
It appears that 6 sessions of TTY are going.  How do I remove all but 2?

---

### Post by bakeneko on 2007-11-11
You can comment out some of the tty's in **/etc/inittab**
(you will need root privileges)

---

### Post by scxtt on 2007-11-11
there is no /etc/inittab in ubuntu (or debian, not sure) ... check out the /etc/event.d/ directory ... it looks like the tty[1-6] files are what cause these to be spawned.

---

### Post by bakeneko on 2007-11-12
Thanks scxtt -- seems I was looking at files left over from Ubuntu 6.06 Dapper.

---

