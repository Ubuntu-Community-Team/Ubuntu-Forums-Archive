---
title: "How do I check the free disk space?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Jokeaflorias on 2007-04-17
I have a simple question, one that I would bet is the most noob question after asked on these forums. How, exactly, can I view the amount of used and free space on Ubuntu partitions of my hard drive?

---

### Post by earobinson on 2007-04-17
```
df
``` also ```
df -f
``` use ```
man df
``` for more info, or you should be able to browse to computer:/// in the file browser

---

### Post by Seisen on 2007-04-17
Applications>Disk Usage Analyzer

---

### Post by UbuntuniX on 2007-04-17
> **earobinson said:**
> ```
df
```

It might help to explain that you enter that in the Terminal.

---

### Post by aysiu on 2007-04-17
A nifty application you might want to look into is FileLight.

Some screenshots:
[http://www.methylblue.com/filelight/images/](http://www.methylblue.com/filelight/images/)

If you don't know how to install it, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Jokeaflorias on 2007-04-17
> **earobinson said:**
> ```
df
``` also ```
df -f
``` use ```
man df
``` for more info, or you should be able to browse to computer:/// in the file browser

Where exactly would I type that in? I just got Ubuntu up and running yesterday and worked with it for two hours, so Im still learning a lot.

---

### Post by Jokeaflorias on 2007-04-17
> **Seisen said:**
> Applications>Disk Usage Analyzer

Thanks. 

I appreciate all the help from you guys. You get responses on these forums faster than I have ever heard of, let a lone seen, on any other forum.

---

### Post by earobinson on 2007-04-17
you can type it in the terminal Applacations->Acessories->terminal sorry!

---

### Post by Seisen on 2007-04-17
You type it in the terminal. Its not your fault you don't understand it took me a little bit of time to learn about the terminal and commands. You will get the hang of it eventually.

---

### Post by notatoad on 2007-04-17
open a folder, look at what it says on the bottom.

---

### Post by earobinson on 2007-04-17
> **Seisen said:**
> You type it in the terminal. Its not your fault you don't understand it took me a little bit of time to learn about the terminal and commands. You will get the hang of it eventually.
Ya I really should have explained better

---

### Post by Pilkjaer on 2008-02-21
thanks a lot. it's really good that you give most explanations from Terminal point of view. So users who are using Ubuntu Server can also use this information.
Thanks! I DO really enjoy my server and it took me like 2 hours to install and set everything up.

---

### Post by Funky91 on 2008-02-21
Go into Places, Computer, right click on the drive and click properties. Like on m$.

---

### Post by Liet_Kynes on 2008-02-21
In a terminal type
```
df -h
```

The -h is for human readable :)

---

