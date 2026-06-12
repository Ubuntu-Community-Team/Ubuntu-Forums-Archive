---
title: "Xubuntu quick question."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-13
Where can i find out my system specifications?Im using xubuntu.

---

### Post by kast on 2007-08-13
**System > Administration > System Monitor** will give you some basic info

---

### Post by Dionysus135 on 2007-08-13
it doesnt say administration.

---

### Post by diatribe on 2007-08-13
sudo lshw 
from a terminal will do it

---

### Post by HermanAB on 2007-08-13
Actually, all the information is in /proc.  Poke around there.

Cheers,

Herman

---

### Post by Dionysus135 on 2007-08-16
how do i do it from a terminal im very new at linux....

---

### Post by Dionysus135 on 2007-08-17
Actually im in the terminal.I found out how much RAM i have but i dont know where to look for the size of my hard drive.

---

### Post by hyper_ch on 2007-08-17
```

df -l

```

---

### Post by Hobo Joe on 2007-08-17
System > Preferences > Hardware information

That will tell you everything you need to know and more.

---

### Post by Dionysus135 on 2007-08-17
i just typed in df -1 and all that came up was
df: invalid option - - 1

---

### Post by hyper_ch on 2007-08-17
it's not a "1" but a "l"

and you can copy'n'paste commands from here ;)

---

### Post by Dionysus135 on 2007-08-17
oh...oops..lol.Well im on the screeen which tells me some info but which is the one that tells me the size of my hard drive?

---

### Post by Dionysus135 on 2007-08-17
Im guessing its the first top one?

---

### Post by HermanAB on 2007-08-17
$ df

That's all.

---

### Post by Dionysus135 on 2007-08-17
> **HermanAB said:**
> $ df

That's all.
I dont see the $ df.Or am i suppose to type that in?

---

