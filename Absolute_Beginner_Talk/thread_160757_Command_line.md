---
title: "Command line"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Topaz on 2006-04-15
In dos you could type dir c: and it would list all directories on c drive.
I have typed ls -lh and it does not list all directories. I know when ubuntu installed it put open office, firefox and alot more on my hard drive. Why can't I see them? You could type tree drive: /f |more and get info. I tried hda1, hdb1 hdc1 and got no such directory. Show me the way.

---

### Post by taurus on 2006-04-15
The way is if you use apt-get or synaptic to install programs, most of them will go in /usr/bin so run this from a terminal (Applications -> Accessories -> Terminal) and you will see the names of all programs in /usr/bin...
```

ls -la | more
(Hit space bar for the next 24 lines...)

```

---

### Post by PhilOSparta on 2006-04-15
At command line try:
    du -H  | more        

for an interesting output.
It shows disk usage by directory.

---

### Post by enyaw on 2006-04-15
[QUOTE=taurus]The way is if you use apt-get or synaptic to install programs, most of them will go in /usr/bin so run this from a terminal (Applications -> Accessories -> Terminal) and you will see the names of all programs in /usr/bin...
```

ls -la | more
(Hit space bar for the next 24 lines...)

```[/QUOTE]
Great information: Thx

---

### Post by Topaz on 2006-04-15
Thank you taurus and PhilOSparta, your commands gave me some good info.

---

### Post by taurus on 2006-04-15
And don't forget if you want to change to a directory, use the cd command as 
```

cd /usr/bin

```

---

### Post by enyaw on 2006-04-15
[QUOTE=PhilOSparta]At command line try:
    du -H  | more        

for an interesting output.
It shows disk usage by directory.[/QUOTE]
Super interesting information.  Thx

---

