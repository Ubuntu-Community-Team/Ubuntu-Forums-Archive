---
title: "some error"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by jwerre on 2006-10-26
I type this:
root@jwerre:~# apt-get install proftpd

and get this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what does all that mean?

anyway, I'm trying to install "proftpd" and can't seem to do it. Does anyone have any ideas?

---

### Post by d3v1ant_0n3 on 2006-10-26
Do you have synaptic or adept open?

---

### Post by qamelian on 2006-10-26
It means you probably have Synaptic or some other package manager open at the same time. Close any othe package managers and try again.

---

### Post by DarkKoopa on 2006-10-26
I'm a n00b but don't you have to use the sudo command?

sudo apt-get install 'package-name'

---

### Post by jwerre on 2006-10-26
How do i know what is running? and once i find that out how do i quit it?

---

### Post by jwerre on 2006-10-26
.

---

### Post by seijuro on 2006-10-26
open a console
run:
```
ps aux
```
find the pid number of the process you want to end then
run:
```
sudo kill <pid_number>
```

---

### Post by jwerre on 2006-10-26
nope, I don't have those running. Any other ideas?

btw, thanks for the help, as you can no doubt see, I'm very new at this.

---

