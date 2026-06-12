---
title: "find a file from the  command line"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-08
I use the command ...

   find  .  -name  nnnnn  -print

... to find a file.  Is there a simpler command than this?  

Carl

---

### Post by tommie74 on 2007-10-08
locate

---

### Post by js_fr on 2007-10-08
"loacte" is faster (and uses less resources) than "find" because it works with a database. Disadvantage: the database might not be up to date (I think by default it is updated once per day). So to be sure that you find a new file also do an "updatedb" before locate:
```
sudo updatedb
locate [pattern]
```
If you just want to know the location of a command (an executable file that is in your PATH) use "which":
```
which [name of command]
```

---

