---
title: "Sources.list"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by TeamMicron on 2007-04-27
I am new to linux/ubuntu and was wondering how I get AVR packages.  I want to uncomment universe and multiverse, but am not sure how to do so.  Thanks for the help.
 TeamMicron

---

### Post by bobplano on 2007-04-27
```
sudo gedit /etc/apt/sources.list
```
and get rid of the # in front of the lines you want. you could also do it the graphical way and go to system>administation>software properties and check it.

EDIT: thanksAlexDe for catching that

---

### Post by Najand on 2007-04-27
Click: System-> Administration -> Software Sources
And then enter your password.
Then try to check all boxes in the page with "Ubuntu software" tab.

---

### Post by AlexDe on 2007-04-27
> 
```
sudo gedit /etc/apt/sources/list
```

and get rid of the # in front of the lines you want. you could also do it the graphical way and go to system>administation>software properties and check it.


Just to avoid confusion he meant:

```

sudo gedit /etc/apt/sources.list

```

---

### Post by bobplano on 2007-04-27
sorry. i'll fix the typo in the post. why do the foward slash and period have to be so close to each other anyway?

---

### Post by Najand on 2007-04-27
LOL... Everyone mistakes... It is Ok... It seems you have been using some drug called Windows a lot. (Joking)

---

