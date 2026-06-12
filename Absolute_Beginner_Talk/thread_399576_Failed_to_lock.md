---
title: "Failed to lock"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Liam1964 on 2007-04-02
I happily installed Feisty Fawn a week or so ago, and managed to get my wireless network set up with all the well written help in this forum. At that stage I thought I was not an idiot after all ... however, I cannot fix this one. HELP please?

When I try to add any new software, using the ADD/REMOVE GUI, I get a message as follows:

Failed to lock /var/cache/apt/archives/lock|

I can find references to similar issues others have had, but this precise issue.

I am reasonably good with computers, but new to Ubutu, so please be gentle :confused:

---

### Post by johnc4510 on 2007-04-02
When you get that msg., do you also have synaptic open?

You can only have one software management program in use at a time.

---

### Post by Liam1964 on 2007-04-02
See how new to this I am ... what is a synaptic?

As far as I am aware, the only thing running is the ADD/REMOVE GUI

---

### Post by johnc4510 on 2007-04-02
Synaptic is the package mgr. or software installer:

System>Administration>Synaptic Package Manager

Don't worry about being new, we all were at one time. Don't be afraid to ask questions and to read and search the forum. 99% of the people here are very helpful.

---

### Post by Liam1964 on 2007-04-02
OK, found what Synaptic is, and no it it not running, and until a few seconds ago, never has been.

---

### Post by johnc4510 on 2007-04-02
Ok, let's see if it's a system problem or an app. problem. Try installing something you couldn't through the add/remove with synaptic. Open synaptic, all of the apps are in alpha order. Hunt for the app. Right click on it and choose mark for install. Then click on apply on the upper bar. 

Note: Close add/remove first

---

### Post by Liam1964 on 2007-04-02
I get the same error, just a little more info. Pasted below

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by johnc4510 on 2007-04-02
Follow taurus's instructions on this thread and see what happens:

[http://ubuntuforums.org/showthread.php?t=391742&highlight=11+Resource+temporarily+unavailable](http://ubuntuforums.org/showthread.php?t=391742&highlight=11+Resource+temporarily+unavailable)

---

### Post by Liam1964 on 2007-04-02
I can upgrade using the sudo commands (I had already found that entry). However I do not have enough knowledge to install new apps using a sudo command. There are several new applications I am trying to install - even a simple codec cannot be added at the moment.

BTW thanks for helping :-)

---

### Post by Liam1964 on 2007-04-02
Can anyone help me with this issue please ...

---

