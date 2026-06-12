---
title: "Autogen with Anjuta problem"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by PleaseEnjoyThis on 2007-09-13
I'm trying to create a new project on Anjuta, but it says I need to get AutoGen and gives me the website.  I tried downloading it, which I thought I did, but it says I still need to download it.  Is there some command line code to download it correctly or something?  thanks.

---

### Post by PleaseEnjoyThis on 2007-09-13
Help

---

### Post by energiya on 2007-09-13
try installing autotools-dev and build-essential
```

sudo aptitude install build-essential autotools-dev

```

---

### Post by PleaseEnjoyThis on 2007-09-13
I still got the same message when I tried to create a new project in Anjuta, it says I need autogen 5.   uuugh.

---

### Post by PleaseEnjoyThis on 2007-09-13
!!! please help I need to program.

---

### Post by energiya on 2007-09-14
Please post the output of
> autogen --help | grep "Ver"

BTW, until you finish dealing with Anjuta you could try [Geany]("http://geany.uvena.de/"). It works nice with all sort of files and it suports C/C++ and other with hotkey compilation, build, run, etc. The only thing it doesn't have is a debugger.

---

### Post by PleaseEnjoyThis on 2007-09-17
bash: autogen: command not found

---

### Post by PleaseEnjoyThis on 2007-09-18
????

---

