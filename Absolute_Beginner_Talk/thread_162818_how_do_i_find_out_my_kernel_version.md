---
title: "how do i find out my kernel version?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-04-19
Hi,
I need to know my kernel version (installing some drivers that require it), how do i find out what it is?

thanks in advance!

---

### Post by angkor on 2006-04-19
type:

```
uname -a
``` 

in a terminal

Edit: Ha, I'm faster than krusbjorn. :)

---

### Post by krusbjorn on 2006-04-19
Open a terminal and type "uname -r".

Edit: Angkor beat me to it ;)

---

### Post by unbuntu on 2006-04-19
alternative:  in terminal and type:
```

cat /proc/version

```

---

