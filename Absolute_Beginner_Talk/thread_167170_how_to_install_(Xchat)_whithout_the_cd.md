---
title: "how to install (Xchat) whithout the cd"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by amubu on 2006-04-27
i uninstalled Xchat by mistake and i want it back. by the way i found this problem with other apps also.
when i try to apt-get it or with synaptic it asks me for the ubuntu cd witch i dont have. (i gave it to a friend). i think its not difficult to install it:confused: 
can you help me pls? thanks

---

### Post by Nikusan on 2006-04-27
[QUOTE=amubu]i uninstalled Xchat by mistake and i want it back. by the way i found this problem with other apps also.
when i try to apt-get it or with synaptic it asks me for the ubuntu cd witch i dont have. (i gave it to a friend). i think its not difficult to install it:confused: 
can you help me pls? thanks[/QUOTE]

You need to remove the cd from your sources list, so that apt/synaptic knows to only look in the online repositories.

First:
```
sudo gedit /etc/apt/sources.list
```
Then remove the line that corresponds to the CD (it's probably the first one). After that you should be good to go.

---

### Post by amubu on 2006-04-27
thank you a lot :D 
...expeditiousness:KS

it is the first one, i ## that

---

