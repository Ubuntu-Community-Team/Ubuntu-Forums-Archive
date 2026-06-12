---
title: "terminal"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-11-13
How do I keep a terminal window open (by open i mean available to take new commands and not be locked to that application) after I have opened an application. I used to use this but have now completely forgotten. If i remember correctly it is something to do with an ampersand (&)?

---

### Post by earobinson on 2006-11-13
```
command &
```

---

### Post by aysiu on 2006-11-13
You also can launch applications with Alt-F2 and then the command name--save you the trouble of launching the terminal first.

---

### Post by turbojugend_gr on 2006-11-13
Anyway if you wish to keep the terminal useful after issuing a command try this:

" give_your_application_command -> CTRL+Z -> bg " this way you put the app in the background and you can continue with your work, you can do this for as many apps you wish, to bring a task on the foreground, issue "jobs" and then "fg NUMBER_OF_THE_JOB_YOU_WANT_TO_BRING_ON_THE_FOREGROUND" and you can manage it again.

I hope this helps...

---

