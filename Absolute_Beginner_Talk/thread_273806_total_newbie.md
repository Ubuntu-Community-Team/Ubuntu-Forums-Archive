---
title: "total newbie"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by hfshacker on 2006-10-08
I started on ubuntu yesterday on an old g3 but I can't seem to find an ide that will install. Please help

---

### Post by meng on 2006-10-08
What have you tried?

---

### Post by hfshacker on 2006-10-08
I tried anjuta but it said "Error: Dependencyis not satisfiable: anjuta" I tried using eclipse with the C++ plugin and it installed fine but wouldn't let me run a local C++ program. I don't know exactly where to llok because I just started yesterday so if somebody good just point me to an ide I could try I'd be very thankful.

---

### Post by mysticrider92 on 2006-10-08
I had trouble getting Anjuta to work also. I got KDevelop from Synaptic and it seems to work well. It will have you install a few KDE packages to work on Gnome, but it is easy to do. Also, you could try Synaptic (If that isn't what you were using) to get Anjuta, but I find it complicated to use, because it needs some other hard to install pakages to make new projects.

[edit] I didn't notice you were using a Mac (I assume that is what the G3 is). This might affect installing these packages, but I don't know for sure.

---

### Post by hfshacker on 2006-10-08
Thanks I'm downloading Konstructor (kde download help) right now.

---

### Post by hfshacker on 2006-10-08
I tried using constructor but when I input the command cd meta/kde;make install it says bash: could not find command make.

---

### Post by hfshacker on 2006-10-08
Can someone please help?

---

### Post by Hranj on 2006-10-08
i had the same problem. when you first install you dont get what you need to perform a make command. you need to install the build essentials. put this in the terminal

```

sudo apt-get install build-essential
```

make should work after that is done.

---

### Post by hfshacker on 2006-10-08
Awesome thanks it's installing now and I'll try kdevelop in one second.

---

