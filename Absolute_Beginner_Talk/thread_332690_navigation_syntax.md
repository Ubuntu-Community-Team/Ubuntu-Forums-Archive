---
title: "navigation syntax"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by GolfGeek on 2007-01-06
I have to aplogize for the stupidity of this one but something just doesn't make sense to me. I am running  a compaq presario 2100 and was trying to install the drivers for the broadcom4306. I found the site, downloaded the file to my desktop. Here is my problem: in a terminal window, how do I access my desktop? For example my laptop logs in as abc and when I open a terminal window I see a prompt of abc@abc-laptop:~$  . When I downloaded the file bcmwl5.zip firefox places in on my desktop. Now I want to copy(move) that file to the /bin or /sbin folder. 

Is it possible to log in to the desktop? I guess what Iam looking for is a primer on hoproblem: w to navigate and copy or move files. The code to install the driver was

sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf

I have tried /abc/desktop/
I have tried ~/desktop/
i have tried ~/abc/desktop/

What is the syntax to get to this point. How can I access this file. Like I said, I know this is a really stupid question.

---

### Post by Sasa_Ivanovic on 2007-01-06
use following commands :
```

cd *location*- moves to the specified directory
mv *source*  *destination*- moves the specified source to the destionation
cp *source*  *destination*- copied  the specified source to the destionation

```
so in your example, go to the desktop would be :
```

cd Desktop

```
also use ls to list directories.

---

### Post by taurus on 2007-01-06
```
cd ~/Desktop
```
Linux/Unix is case sensitive...

---

### Post by eekbot on 2007-01-06
NOTE:  make sure to capitalize the 'D' in Desktop too

---

### Post by GolfGeek on 2007-01-06
Sasa
Thanks for the quick reply. Still looking for a good primer on commands

---

### Post by GolfGeek on 2007-01-06
Another note: totally forgot about case sensitivity. Am in such a habit of lower case for everything
Thanks again

---

### Post by hyper_ch on 2007-01-06
maybe this here:

[http://www.ccsf.edu/Pub/Fac/unix2.html](http://www.ccsf.edu/Pub/Fac/unix2.html)

---

### Post by wesley_of_course on 2007-01-06
Would this help ?          [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

