---
title: "Finding RAM and CPU info"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by fmalan on 2006-01-10
Hi!

I'm new to Linux, and want to see some info on my machine's CPU and memory. Where do I do this? As far as I can remember it is under /proc/cpuinfo and /proc/meminfo or something like that, but when I access /proc (even as superuser) I do not get these fields.

I get something like:
Display all 112 possibilities? (y or n)
1/         2/         7480/      8243/      8460/      8543/      8835/
1013/      3/         7495/      8252/      8461/      8546/      9/
1014/      3633/      7512/      8266/      8463/      8552/      acpi/
1019/      3785/      7514/      8279/      8466/      8560/      asound/
1020/      4/         7527/      8287/      8468/      8567/      bluetooth/
1027/      5/         7540/      8301/      8472/      8569/      bus/
1028/      5165/      7545/      8333/      8474/      8571/      driver/
13/        5523/      7556/      8352/      8480/      8573/      fs/
138/       5524/      765/       8388/      8493/      8575/      ide/
139/       5525/      7890/      8389/      8518/      8577/      irq/
142/       5526/      7895/      8390/      8523/      8584/      net/

Where is this info hiding?
F

---

### Post by ape on 2006-01-10
These both should be present under the /proc directory.  Change to the /proc directory and type `cat meminfo` or `cat cpuinfo`.

---

### Post by aysiu on 2006-01-10
This may be overkill, but you can also try opening a terminal and typing ```
top
```

---

### Post by GodsDead on 2007-12-13
this may have been posted mission ago, but thanks =] simple, "top" 
haha

---

### Post by The Cog on 2007-12-13
How about 
> lshw | less

---

