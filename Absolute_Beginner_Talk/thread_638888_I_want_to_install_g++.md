---
title: "I want to install g++"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-12-12
I want to install g++, but when I try to

```
 sudo apt-get install g++ 
```

It ask me for the Ubuntu CD. I don't have it (since a friend of mine has it). I already trying updating apt-get, but is there a way to install g++ without the install cd?

---

### Post by mali2297 on 2007-12-12
In Synaptic, go to Settings -> Repositories and uncheck the boxes for CD.

---

### Post by oldos2er on 2007-12-12
Go into your Software Sources and uncheck the box next to cd-rom. Make sure all other sources are enabled. Run 'sudo aptitude update' before you run 'sudo aptitude install g++'.

---

### Post by seanc7 on 2007-12-12
Now I'm pretty new to Ubuntu but I think I can help you. The more senior members can correct me if my advice is wrong. :)

In Synaptic, you can choose what repositories to use for updating software. I think there's an option for the Ubuntu CD. So if you uncheck that option and probably do a refresh you should be able to download everything from the Internet instead of it asking you for the CD.

Sean

---

