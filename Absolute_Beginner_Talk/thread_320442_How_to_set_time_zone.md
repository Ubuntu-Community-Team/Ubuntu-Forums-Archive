---
title: "How to set time zone?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by woland on 2006-12-17
How to set time zone in Ubuntu server in CLI mode?

I'm connecting to my Ununtu server via SSH and I want to set the correct time and time zone.

Thanks in advance.

---

### Post by taurus on 2006-12-17
```
sudo date **121710452006**
-or-
man date
(for more info...)
```
where 12 is the month, 17 is the day, 10 is the hour, 45 is the minute, and 2006 is the year!

---

### Post by woland on 2006-12-17
Taurus, thanks for the response, unfortunately it doesn't answer my question.
I know how to set time, but I need to set the **timezone**.
Right now the server is set to EST. I need it to be GMT +2.

---

### Post by msak007 on 2006-12-17
Run
```
sudo tzconfig
```
and then choose your desired timezone.

---

### Post by woland on 2006-12-17
msak007, thank you  very much!

---

### Post by msak007 on 2006-12-17
> **woland said:**
> msak007, thank you  very much!
No problem, glad it helped. I learned that command early on and use it after a new install because the installer forces me to choose a city instead of a timezone (e.g. New York instead of EST). I really wish they'd change that...

---

### Post by alimadzi on 2007-11-15
I'm so glad I read this before launching into the following series of manual steps...

[http://www.wikihow.com/Change-the-Timezone-in-Linux](http://www.wikihow.com/Change-the-Timezone-in-Linux)

Clearly 'tzconfig' is a LOT easier... ;)

---

### Post by golfing22 on 2007-12-17
For future reference in gutsy it is "tzselect" instead.

---

### Post by zcionn on 2008-01-03
tzselect only gives you a view of the time at a particular timezone.

to change the timezone use "dpkg-reconfigure tzdata" instead

---

