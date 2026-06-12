---
title: "changing file permissions"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-04-09
ok, i'm sure this question has been asked before, bit i have done some extensive reading and can't find exactly what i'm looking for. i am having trouble changing the file permissions to where i can write to the file. i'm currently running Fluxbuntu Gutsy Gibson. if someone would be kind enough to post the terminal command to change the file permission so that all users can write to it it would be greatly appreciated.

---

### Post by scragar on 2008-04-09
```
chmod +w **file**
```

---

### Post by Joeb454 on 2008-04-09
Couldn't have put it any simpler myself. There's a lot more to chmod than that (I've played with it on my server :p)

It makes a nice change to see somebody asking for a terminal command rather than a GUI method though :D

---

### Post by rockerphil on 2008-04-09
lol joeb545, thanx, i much prefer the terminal over a GUI. a GUI is just another program that can have problems where as the terminal allows me to talk directly with my system

---

### Post by Joeb454 on 2008-04-09
Very true :)

I didn't particularly like the terminal at first, but realised it'd be easier if I got to know it :p

---

### Post by scorp123 on 2008-04-09
> **rockerphil said:**
>  a GUI is just another program that can have problems where as the terminal allows me to talk directly with my system Exactly. Or how a Sith Lord would put it: > GUI's are a lie, they're just front-ends to the shell.
Through the shell, I gain sudo.
Through sudo, I gain power.
Through power, I gain root.
Through root, my chains are broken.
uid=0 shall free me. :lolflag:

( search for "Sith Code" in Google to find the original ... "Peace is a lie ... " ... )

---

### Post by bodhi.zazen on 2008-04-09
+1 Fluxbuntu Power To The People !!!!!!!!!!

---

### Post by lackofcreativity on 2008-04-09
Long Live the Terminal!!!!!!

---

### Post by waynep on 2008-04-09
> **scragar said:**
> ```
chmod +w **file**
```

To add to this very correct answer . . . you may have to use sudo if you don't own the file. 

-wayne

---

