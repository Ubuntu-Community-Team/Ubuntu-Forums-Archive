---
title: "How to add GUI after server install"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by JonRohan on 2006-02-19
Hi, 

I've been having a good play around with ubuntu this afternoon. 

Initially I started off with a skinny install with no gui and stuff. I'd like to now add the gui but cant seem to track a thread down to give me instructions.

If anyone can point me in the right direction i'd be most grateful. 

Thanks, 

Jon

---

### Post by cwaldbieser on 2006-02-19
[QUOTE=JonRohan]Hi, 

I've been having a good play around with ubuntu this afternoon. 

Initially I started off with a skinny install with no gui and stuff. I'd like to now add the gui but cant seem to track a thread down to give me instructions.

If anyone can point me in the right direction i'd be most grateful. 

Thanks, 

Jon[/QUOTE]

Try
```

$ sudo apt-get install ubuntu-desktop
OR
$ sudo apt-get install kubuntu-desktop

```

---

### Post by Perfect Storm on 2006-02-19
Perhaps something lighter if he is go to run a server.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by JonRohan on 2006-02-19
excellent. Thanks guys. 

Its not a real server im just messing around. :).

For some reason the sudo apt-get install xubuntu-desktop wasn't found. :S

---

### Post by mushroom on 2006-02-19
Do you have the universe repository enabled?

---

