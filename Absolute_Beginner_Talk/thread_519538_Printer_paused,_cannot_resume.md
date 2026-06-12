---
title: "Printer paused, cannot resume"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by aitorcalero on 2007-08-07
I have installed a new printer. At first it works fine, but suddenly, It does not work at all. It is always in paused state, and after reading almost every previous post about this topic in this forum, I am not able to resume it. Is this a common bug with cups or something like that?

---

### Post by xopher_mc on 2007-08-07
try typing this into the terminal

[HTML]sudo /etc/init.d/cupsys restart[/HTML]

---

### Post by aitorcalero on 2007-08-07
Thank you! I've already try that unsuccessfully. It seems to be that sort of weird problems... :confused:

---

### Post by xopher_mc on 2007-08-07
any chance of more details, like which printer your using ect..

---

### Post by aitorcalero on 2007-08-08
I think it is not a printer problem, because it is used by other users in my company (it is a network printer). It is a Gestetner DSm645/645G PXL. I am using the same printer configuration of a workmate (which works perfect for him). 
As I said in my first email, I have successfully print documents, but It seems that there is a problem with the queue, can I flush / delete printer queues?

---

### Post by aitorcalero on 2007-08-08
Problem Solved!!!!
I find a clue here ([https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/24887]("https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/24887"))
The point was to launch "gnome-cups-manager" with gksudo:
```
gksudo gnome-cups-manager
```
I guess that if I add my user to cups groups it will also works in the future without gksudo.
:)

---

