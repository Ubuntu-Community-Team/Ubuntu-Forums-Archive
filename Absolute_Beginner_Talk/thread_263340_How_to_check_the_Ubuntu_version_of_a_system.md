---
title: "How to check the Ubuntu version of a system?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Andrea_44 on 2006-09-23
What command could you used to check the Ubuntu version of a system?


Thanks,

Andrea

---

### Post by empcrono on 2006-09-23
> **Andrea_44 said:**
> What command could you used to check the Ubuntu version of a system?


Thanks,

Andrea

im not sure of a command that just does it. however i know a way to know.
go to terminal or konsole

type in 

sudo nano /etc/apt/sources.list

if it says dapper in the repository list (dapper at the end of address or somthing) if it says somthing else then thats what your running that.

---

### Post by bodhi.zazen on 2006-09-23
In a terminal type:

```
cat /etc/issue
```

---

### Post by Andrea_44 on 2006-09-23
Cheers:>

Andrea

---

### Post by David Corrales on 2006-09-23
**lsb_release -a** works too.

---

### Post by MWAAAHAAA on 2006-09-23
> **empcrono said:**
> im not sure of a command that just does it. however i know a way to know.
go to terminal or konsole

type in 

sudo nano /etc/apt/sources.list

if it says dapper in the repository list (dapper at the end of address or somthing) if it says somthing else then thats what your running that.

To prevent "accidents" from happening you should never start a file editor to view a file you are not going to modify. Use 'cat' or 'less' or 'more' instead.

---

### Post by wildseven on 2006-09-23
uname -a works aswell


wo0ps, sorry heh~ i read wrong, i thought he meant kernel

---

### Post by barnacleJim on 2007-09-03
> **David Corrales said:**
> **lsb_release -a** works too.
the same info is located at /etc/lsb-release

---

### Post by ramjet_1953 on 2007-09-03
Navigate to [COLOR="Blue"]System>About Ubuntu[/COLOR]

In the second Paragraph down, after the Contents it tells you the version number.

Regards,
Roger :cool:

---

