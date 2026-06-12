---
title: "How to kill all poceses"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-19
Can someone tell me how to end all of the proceces?

---

### Post by overdrank on 2007-05-19
> **mojo123 said:**
> Can someone tell me how to end all of the proceces?

Hi ctrl,alt,backspace  should do it, it will restart X!:guitar:

---

### Post by mojo123 on 2007-05-19
ik that but i want to end all proccecs in this sesstion

---

### Post by houstonbofh on 2007-05-19
Power button?

You can not stop everything, without stopping **everything.**  You can do a 'ps -ef | grep username' and kill stuff, but not the process you are using to kill stuff.  Perhaps if you tell us what problem you need to solve we can give you a better answer.

---

### Post by juxtaposed on 2007-05-19
You can do it manually by doing killall firefox (replace firefox with what you want to close) or, i've heard you can do killall -all to stop everything. I can't confirm that though.

---

### Post by woland on 2007-05-19
The cli command is "killall".
Type ```
killall --help
``` to get help on all the options.
One that I think that you might want to use is: ```
killall -u USERNAME
```
this one will kill all the processes prom any given user.

---

