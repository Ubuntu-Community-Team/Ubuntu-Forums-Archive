---
title: "[SOLVED] kmail gives me a warning"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-09-16
when i open kmail i get this warning 

Kontact already seems to be running on another display on this machine. Running Kontact more than once can cause the loss of mail. You should not start Kontact unless you are sure that it is not already running.

i am running kubuntu desktop,there is no other applications open  :confused:

thanks for any help

---

### Post by por100pre1 on 2007-09-16
> **nikef said:**
> when i open kmail i get this warning 

Kontact already seems to be running on another display on this machine. Running Kontact more than once can cause the loss of mail. You should not start Kontact unless you are sure that it is not already running.

i am running kubuntu desktop,there is no other applications open  :confused:

thanks for any help

I may be wrong, but try this first:

```
pkill kontact && pkill kmail
```

logout and log back in... :-k

---

### Post by nikef on 2007-09-16
Thanks very much for your help

i used the code,loged out and back in on my pc,all is working great  :)

will mark solved

---

