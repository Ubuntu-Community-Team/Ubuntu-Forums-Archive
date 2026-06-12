---
title: "internal error report"
date: 2014-11-09
forum: Apple Hardware Users
---

### Post by rican-linux on 2014-11-09
Everytime I login to my desktop I get this pop up saying there is an internal error. It looks there is an issue with lightdm. I cannot capture the report, it just asks me if I want to send the report. I cannot anything in /var/log that help me know what is going on. Does anyone know where I can go find to find out what is the issue?

---

### Post by ibjsb4 on 2014-11-10
Reset 'Apport'.  Remove the file /var/crash/.apport

Or just turn off apport.

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

[http://ubuntuforums.org/showthread.php?t=1982373&p=11951735#post11951735](http://ubuntuforums.org/showthread.php?t=1982373&p=11951735#post11951735)

---

### Post by rican-linux on 2014-11-10
Thanks! I just did that. Hopefully that should fix it.

---

### Post by rican-linux on 2014-11-10
> **ibjsb4 said:**
> Reset 'Apport'.  Remove the file /var/crash/.apport

Or just turn off apport.

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

[http://ubuntuforums.org/showthread.php?t=1982373&p=11951735#post11951735](http://ubuntuforums.org/showthread.php?t=1982373&p=11951735#post11951735)

This has worked thanks!

---

