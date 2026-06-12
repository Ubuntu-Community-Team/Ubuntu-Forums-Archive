---
title: "Running applications"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-03-11
I downloaded an application called Ecasound.  It shows to have been installed.  How do I go about running it?
Caruso

---

### Post by AndyCooll on 2007-03-11
Open up a terminal and try typing "ecasound" (without the speech marks).

:cool:

---

### Post by carusoswi on 2007-03-11
I get the message 'command not found.'
If I click on the Firefox download box where ecasound shows to have completed its download, I can open the file and it states that it has already been installed, so, I am wondering how I go about making it run.
Thanks for your reply, let me know if I'm missing something.

Caruso

---

### Post by AndyCooll on 2007-03-11
There are a few possibilities to try:
1). Try typing the exact path of the app executable. It may well be something like:
```
cd /usr/bin
ecasound
```
2). Sometimes logging out and logging back in places an icon in the Applications menu.
3). Try re-installing the program using Synaptic (System > Administration > Synaptic Package Manager) since it's actually in the repositories. Installing this way usually puts startup icons in the appropriate places.

:cool:

---

