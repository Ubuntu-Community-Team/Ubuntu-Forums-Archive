---
title: "screenshot capture"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by actioncomics on 2007-05-15
I was wondering if there is a way to capture a screenshot at regular intervals.  every XX mins/secs. take a screenshot and save it in a folder.

---

### Post by DaveyG on 2007-05-15
Hi there, i dont know about every few min/secs but if you press one of the F8 or F10 buttons it will take a screenshot,

Davey

---

### Post by actioncomics on 2007-05-15
I was wanting to use it to monitor my son on his computer.  I can move him over to linux if i can find a way to monitor his computer.  screenshots were the easiest because it caught what what typed and what he was looking at all at the same time.

so unfortunately pressing a key would not work.  thanks for the reply tho.

---

### Post by racyrefinedraj on 2007-05-15
install scrot

```
sudo aptitude install scrot
```

this is a command line app that takes screenshots. Running it with no arguments, IE

```
scrot
```

timestamps the screenshot and saves it in the current directory. 

Between that and cron (scheduling program) you should be able to do what you want to do.

---

