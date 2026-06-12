---
title: "using gksu to run a jar file"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Zyphrexi on 2007-02-25
ok so I'm trying to run this

```
gksu java -jar /usr/share/games/crossfire/CFJavaEditor/CFJavaEditor.jar
```

with a shortcut, but it doesn't seem to work. Usually I'd do it in console with sudo, is there any other special thing i have to do that i'm not doing right?

---

### Post by Stemp on 2007-02-25
If you do that command in console ? is it working ?

---

### Post by Zyphrexi on 2007-02-25
no

---

### Post by anubhavrocks on 2007-03-23
first of all check  that you have execute permissions for the file or you can give this command and then run

chmod +x /usr/share/games/crossfire/CFJavaEditor/CFJavaEditor.jar
and then try to run using you usual way
sudo  java -jar /usr/share/games/crossfire/CFJavaEditor/CFJavaEditor.jar

---

### Post by anaconda on 2007-03-23
hmm.. interesting. I always use **gksudo** not gksu, but it seems both of them work.. atleast from the terminal.

---

### Post by anubhavrocks on 2007-03-26
> **anaconda said:**
> hmm.. interesting. I always use **gksudo** not gksu, but it seems both of them work.. atleast from the terminal.

Both are the same actually..

gksudo is a soft link to gksu

lrwxrwxrwx 1 root root 4 2007-02-10 05:37 /usr/bin/gksudo -> gksu

---

