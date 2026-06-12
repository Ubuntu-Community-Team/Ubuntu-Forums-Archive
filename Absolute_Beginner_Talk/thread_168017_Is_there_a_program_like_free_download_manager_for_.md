---
title: "Is there a program like free download manager for ubuntu?"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-29
Hi all, I am trying to find a program like free download manager FDM for firefox in ubuntu.  Right now FDM is not supported for linux.  I am trying to download all pictures from a website but with download 4 X I end up getting everything from the website.

---

### Post by cwaldbieser on 2006-04-29
[QUOTE=racermike1967]Hi all, I am trying to find a program like free download manager FDM for firefox in ubuntu.  Right now FDM is not supported for linux.  I am trying to download all pictures from a website but with download 4 X I end up getting everything from the website.[/QUOTE]
Sounds kind of like wget, but there are a whole bunch of tools like this.  Type this in a terminal to get an idea of some:
```

$ apt-cache search download | grep download | less

```
This searches your repository cache for descriptions containing "download".  Type 'q' to quit.

---

### Post by The Mekon on 2006-04-29
I just used Synaptic and searched for "download manager" which gave several programs.  I have just tried gwget which works quite well and provides automatic restart etc.

---

### Post by Ozitraveller on 2006-04-29
d4x is what I use.

---

