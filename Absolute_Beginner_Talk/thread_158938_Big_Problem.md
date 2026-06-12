---
title: "Big Problem"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by LiquidFlame on 2006-04-12
I don't know what happend but when I try to click on Synaptic Packet Manager I get this error: > Cannot launch entry

Details: Failed to execute child process "gksudo" (No such file or directory)

What does this mean and please help

---

### Post by dermotti on 2006-04-12
Hmm did gksudo get deleted? 

try 

**sudo synaptic** from command line

---

### Post by Sef on 2006-04-12
Try from the terminal:  

sudo apt-get update

sudo apt-get install gksudo

Terminal:  Applications > Accessories > Terminal

---

### Post by aysiu on 2006-04-12
[QUOTE=Sef]Try from the terminal:  

sudo apt-get update

sudo apt-get install gksudo

Terminal:  Applications > Accessories > Terminal[/QUOTE] Wouldn't it be this? ```
sudo apt-get update
sudo apt-get install --reinstall gksu
```

---

