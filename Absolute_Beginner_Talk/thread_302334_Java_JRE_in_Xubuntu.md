---
title: "Java JRE in Xubuntu"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by fransk on 2006-11-18
Hi,

I'm trying to install JRE in Xubuntu Dapper for weeks. I've read all the messages related to that. But I allways get stuck in problems with dependent files. Please, can somebody tell me step-by-step what should I do to be sucessfull with this task? I have also to get it working with Firefox.

Thank you.

---

### Post by localuser on 2006-11-18
What have you already tried?

---

### Post by tktino on 2006-11-18
try automatix.. it will install it for you. I am noob too.. Noob Power

---

### Post by fransk on 2006-11-21
I've tried Synaptic and fail... downloading from the Java website and follow the instructions and fail... tried the sudo apget install java... fail. But I've learned how to install Automatix for Xubuntu Dapper and it was the final solution. Now, is everything ok. Thank you all.

---

### Post by Ben Sprinkle on 2006-11-21
Download JRE.
Right click the .bin and click properties => executable.
Go in a terminal.
```

sudo ./jre.bin

```
There you go. To run:
```

'/home/$USER/Desktop/jre/bin/java' yourclass.class

```
Change to the correct folders of course. :)

---

