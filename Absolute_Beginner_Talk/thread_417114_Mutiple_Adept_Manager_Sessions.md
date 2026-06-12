---
title: "Mutiple Adept Manager Sessions?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by mistergq on 2007-04-21
I just installed Kubuntu 7.04.  I wanted to install firefox, evolution, and java.  I selected all three at once (probably a mistake).  there was an error, gave me a log window, I closed it.  I then clicked on Adept Manager again, and got the following error:

> Another process is using the package system database (probably some other Adept application or apt-get or aptitude).  Please close the other application before using this one.

So I can't find another one, log out, try again, same error.  Restart, same error.

Its been awhile since I have used Ubuntu, so I cannot remember if there is a taskmanager to see what is running, but something is preventing me from bringing up.

How can I find or kill the other process?

---

### Post by Nythain on 2007-04-21
sudo dpkg --configure-a
sudo aptitude clean

---

### Post by mistergq on 2007-04-21
Found the answer, needed to run the following command line

```
 sudo dpkg --configure -a 
```

Fixed the problem.

---

### Post by mistergq on 2007-04-21
> **Nythain said:**
> sudo dpkg --configure-a
sudo aptitude clean Thanks. I have to get back into the mode of thinking command line!

---

### Post by Nythain on 2007-04-21
hehe... my desktop environment is a pretty way for me to browse the web and listen to music... its amazing how dependent i've become on the command line in a just a little under a year of running ubuntu... yakuake is my freind

---

