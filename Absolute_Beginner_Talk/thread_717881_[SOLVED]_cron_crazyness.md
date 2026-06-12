---
title: "[SOLVED] cron crazyness"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2008-03-07
Ive got cron running getmail every 5 minutes. How can i stop it emailing me to say it has recieved mail? I dont mind it emailing me problems but damn do i want these! :O

---

### Post by Oldsoldier2003 on 2008-03-07
> **dgrafix said:**
> Ive got cron running getmail every 5 minutes. How can i stop it emailing me to say it has recieved mail? I dont mind it emailing me problems but damn do i want these! :O

add this to the crontab line for the job:

```
>/dev/null 2>&1
```

---

### Post by Dr Small on 2008-03-07
```
*crontime* command **2& > /dev/null**
```

---

### Post by Oldsoldier2003 on 2008-03-07
> **Dr Small said:**
> ```
*crontime* command **2& > /dev/null**
```

lol i think we just said the same thing in two different ways :)  don't you just love how flexible linux the linux shell commands can be?

---

### Post by dgrafix on 2008-03-07
aha :)

---

### Post by Dr Small on 2008-03-07
> **Oldsoldier2003 said:**
> lol i think we just said the same thing in two different ways :)  don't you just love how flexible linux the linux shell commands can be?
Lol, yeah. There are all sorts of different ways to pipe the output to /dev/null :)

---

### Post by dgrafix on 2008-04-06
OK i just tried both but they just stop the command running.

Here is how ive got it:

*/5 *   * * *   dan    getmail 2& > /dev/null


´

---

### Post by Oldsoldier2003 on 2008-04-06
> **dgrafix said:**
> OK i just tried both but they just stop the command running.

Here is how ive got it:

*/5 *   * * *   dan    getmail 2& > /dev/null


´

try it this way and see if it works?

```
*/5 *   * * *   dan    getmail >/dev/null 2>&1
```

---

