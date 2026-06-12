---
title: "Wine emulator where is it ?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by #1slug on 2006-07-12
First question:
I isntalled it, and even updated it through the synaptic package manager, but is there a gui for this program , I mean how do I find it ? 

Second question:
 How do I launch it or get it to emulate say quickpar.

 Thanks for any help.

---

### Post by o_fortuna on 2006-07-12
The first step to installing wine is to open up a terminal (Applications--Accessories--Terminal) and type
```
winecfg
```
This will take a moment, but it will configure wine to work. Then, when you have the program you want to run, just double click the .exe file, and Wine should run it automatically. Just remmeber that Wine is far from perfect, and may not run some programs at all.

---

### Post by Kilz on 2006-07-12
> **#1slug said:**
> First question:
I isntalled it, and even updated it through the synaptic package manager, but is there a gui for this program , I mean how do I find it ? 

Second question:
 How do I launch it or get it to emulate say quickpar.

 Thanks for any help.
Wine isnt a gui program. You cant launch it. It runs silently in the background and lets you run some windows programs on linux. 
To install a program, find the install/setup exe. Right click on it then select Open with Other Application. The application list will pop up. At the bottom click on use custom command. Type wine in the box that opens. then click open. The install program will start.
you only have to do that once then wine is assoicated with exe files. doubble clicking on them in the future will automaticly start wine in the background.

---

### Post by aysiu on 2006-07-12
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by #1slug on 2006-07-13
Just wanted to say thanks,your responses realy do help. Thanks:)

---

