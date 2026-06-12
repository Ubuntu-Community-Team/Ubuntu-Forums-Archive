---
title: "Help with Running Apps through Terminal"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by naraic on 2007-06-10
Hello.  
My first post, and it's to start a new thread...  I would have prefered not to do this, but I couldn't find anything on the same topic when i searched.  Sorry if i'm doing something wrong.

Anyway, heres my question:  When i attempt to run an application through terminal, such as Firefox, or Gaim, the application seems to depend on the running of the terminal window from which it was started.  I was wondering if there was any way of running an application in this manner so that the terminal window can still be used for other commands and the application does not close when the terminal window is closed.

Sorry for any incorrect terminology, but I'm totally new to the whole GNU/Linux scene.
I thank you in advance for your help  :)

naraic

---

### Post by Outrunner on 2007-06-10
```
firefox &
```

```
gaim &
```

---

### Post by eagleeyed on 2007-06-10
Thanks Outrunner,

I also just learnt a new thing.

Stewie
Eagleeyed

---

### Post by naraic on 2007-06-10
Thank you, fr the answer and the quick reply.   Thats really helpful.

---

### Post by Nythain on 2007-06-10
quick question, will that method work with wine???
like say
wine ~/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe &
nothing sucks worse than using up a terminal to run utorrent and have to load another one to do anything else

---

### Post by FleetAdmiral74 on 2007-06-10
> **Nythain said:**
> quick question, will that method work with wine???
like say
wine ~/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe &
nothing sucks worse than using up a terminal to run utorrent and have to load another one to do anything else

I can think of one way to find out that would take no longer then, say, posting a question on the forum  ;)

---

### Post by Kobalt on 2007-06-10
> **Nythain said:**
> nothing sucks worse than using up a terminal to run utorrent and have to load another one to do anything else
On one hand you don't  need to use a windows app in Ubuntu, there are very good alternatives such as Transmission or KTorrent. 
On the other hand, you don't need to open a new Terminal, just open a new shell : Shift+Ctrl+T

---

