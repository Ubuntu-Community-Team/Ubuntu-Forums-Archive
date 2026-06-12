---
title: "openoffice startup"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by ubuntosh on 2006-06-07
Hello everybody

I'd like to know how to disable openoffice from starting every time I boot my laptop and also why this happened, because I don't remember configuring it to do so.

thnx:confused:

---

### Post by xXx 0wn3d xXx on 2006-06-07
Install bum:
> sudo apt-get install bum
and then run it by going under Sysem > Administration > Boot up Manager. Then uncheck openoffice. If that doesn't work, open open office, go under Options > Memory and uncheck "preload at startup."

---

### Post by ubuntosh on 2006-06-08
Thnx. 
I tried but it didn't work. Bum doesn't display any process or info related to openoffice at startup and the OO box for preload at startup wasn't checked. 

I tried to solve it by unistalling OO writer and after that another OO application, in this case OO presentation, starts up.
So i unistalled the whole OO suite by using sinaptic and then reinstalled everything hoping this would solve the issue but it did not. What should I do now? I need help please

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=ubuntosh]Thnx. 
I tried but it didn't work. Bum doesn't display any process or info related to openoffice at startup and the OO box for preload at startup wasn't checked. 

I tried to solve it by unistalling OO writer and after that another OO application, in this case OO presentation, starts up.
So i unistalled the whole OO suite by using sinaptic and then reinstalled everything hoping this would solve the issue but it did not. What should I do now? I need help please[/QUOTE]
Try following [ this howto. ](http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+boot+process) Make sure the line with open office has no X's on it. Don't disable things that you need.

---

