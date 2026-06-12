---
title: "Run in a terminal"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by larini on 2007-05-03
Hi, I am wanting to associate an application to a extension, but when I execute, the application runs underneath and I cant see nothing happens. It wanted to know if has a way to associate the application and when execute it (in nautilus) a terminal open to know that some thing is executing.
Thanks.

---

### Post by yota on 2007-05-03
Hi, you can for sure:

when you create the application luncher select "application in the terminal" as the application type (I translated from italian back to english, so it may not be accurate).

Hope this helps!

---

### Post by larini on 2007-05-03
Is not exactly this I'm needing.
Look this screen, I need to associate a aplication but this application must run in a terminal.

---

### Post by zvacet on 2007-05-04
You are trying to find app wihc open XML documents.If it is not on the list, and you know that you have one type name of app or navigate to the place where it is.Usualy apps are stored in usr/bin but if you don´t find it there search other places.

---

### Post by yota on 2007-05-04
> **larini said:**
> Is not exactly this I'm needing.
Look this screen, I need to associate a aplication but this application must run in a terminal.

Oh, sorry I didn't understand it.

To achieve what you need you can launch the application inside a gnome-terminal, let's say for instance that I want to edit a txt file with vi, I should associate .txt with:
```

gnome-terminal -x vi

```
Let me know if this works!

---

### Post by larini on 2007-05-05
yota, this works greate! Thanks.

---

### Post by larini on 2007-05-14
Using gnome-terminal works, but I need that the terminal window remains opened at end of command.
Is this possible?

---

