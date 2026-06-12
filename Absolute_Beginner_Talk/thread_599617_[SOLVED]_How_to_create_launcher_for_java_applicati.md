---
title: "[SOLVED] How to create launcher for java application?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Malefiz on 2007-11-01
Hallo!

I have a little problem of convenience on my hands:
As an avid Scrabble player using WordBiz, I would like to create a launcher for the application that allows me to run the (java) application by, preferably, clicking on a Desktop icon.

I tried using the "Create Launcher" function, but am seriously stuck as to what to type into the Command field. Surely, there must be some string of commands that'd make it possible to run WordBiz that way?! 

Folks, please help! I'm tired of a) clicking myself through to running the application and b) using the command line to just launch WordBiz.

Any suggestions are highly appreciated!

Thanks,
Malefiz

---

### Post by Inxsible on 2007-11-01
1) Right click on desktop -- > Select Create Launcher

2) In the command box, enter the command that you use in the terminal.

3) Give it a nice little icon and you are done.

---

### Post by ddrichardson on 2007-11-01
```
java /path/to/jar.jar
```

---

### Post by Malefiz on 2007-11-01
Hi!
Thanks for the replies!
I finally got it working.

Tried the suggested lines before but it failed to work. Then tried running it from command line and when that failed as well, it finally made "click" in my tired brain. Problem was I had SunJava AND GCJ installed. Once I removed the latter, the problem solved itself. I now have it working as intended!

Cheers,
Malefiz

---

### Post by Inxsible on 2007-11-01
> **Malefiz said:**
> Hi!
Thanks for the replies!
I finally got it working.

Tried the suggested lines before but it failed to work. Then tried running it from command line and when that failed as well, it finally made "click" in my tired brain. Problem was I had SunJava AND GCJ installed. Once I removed the latter, the problem solved itself. I now have it working as intended!

Cheers,
Malefiz
Glad to hear. Please mark your thread as solved. :)

Thread Tools -- > Mark thread as solved.

---

