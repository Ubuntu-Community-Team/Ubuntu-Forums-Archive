---
title: "[SOLVED] Command to view SSH connections"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Blue Sassley on 2007-10-21
Can someone please tell me what the command is to see current SSH connections to a ubuntu box?

Thanks for the help,
Blue

---

### Post by HermanAB on 2007-10-21
nmap, tcpdump.

---

### Post by p_quarles on 2007-10-21
I use:
```
netstat -tunva
```

---

### Post by bodhi.zazen on 2007-10-21
Well, you can also enter ```
who
``` to see who is logged in, although this does not list connection.

---

### Post by Blue Sassley on 2007-10-21
Thanks guys!

---

### Post by Dr Small on 2007-10-21
```
who
```
```
users
```

---

