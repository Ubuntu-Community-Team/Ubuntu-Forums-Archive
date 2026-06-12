---
title: "Failure in Software Management System"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Faizal4in on 2007-12-11
Hi All,

Please find the screenshots of the errors that I found.
I would appreciate your help.

Regards,

Faizal

---

### Post by wormser on 2007-12-11
The error is telling you that something is wrong on line 47 of your /etc/apt/sources.list.  That file has your repository list on it.  The other one is recommending you run sudo apt-get update and sudo apt-get install -f.  First you should fix the sources.list file then run those 2 commands.

```
gksudo gedit /etc/apt/sources.list
```

Look at line 47.  It probably looks different then the rest.  If you need help with it then post the file.  Then run the 2 commands.

```
sudo apt-get update
```
```
sudo apt-get install -f
```

---

### Post by kpkeerthi on 2007-12-11
Can you post the content of your sources.list here (Pls use ```
 tag)

From terminal.
[code]
gedit /etc/apt/sources.list

```

---

### Post by 357mag on 2007-12-11
That's Linux for you. Problems galore. It deserves all the bad press it gets.

---

