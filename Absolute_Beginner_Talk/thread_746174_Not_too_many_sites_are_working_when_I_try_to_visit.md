---
title: "Not too many sites are working when I try to visit them."
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by lase on 2008-04-05
I can't seem to connect to about 75% of the sites I try to visit since this morning 0.o

AIM Won't connect but MSN will. I can't connect to my email yet ubuntu.com works....?

Any reason why? I checked it on another computer and they work on there...

---

### Post by Michael.Godawski on 2008-04-05
What browser are you using? Did you try another one?
Did you installed some network relevant updates?
Can please post the result of these terminal commands?

```
iwconfig
sudo lshw -C network
```

---

### Post by lase on 2008-04-05
Using firefox. Just installed a bunch of updates so I don't remeber.

```

lase@lase-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lase@lase-desktop:~$ sudo lshw -C network
[sudo] password for lase:
lase@lase-desktop:~$      

```

The sudo lshw -C network had showed some changing text but that was it.

---

### Post by strick242 on 2008-04-05
I'm kinda having the same problem since installing the updates.  Instead of sites not working though, griffith and gcfilms can't find information on the internet....weird.

---

### Post by superprash2003 on 2008-04-05
it could be a DNS problem. try changing your DNS servers to OPENDNS.

---

### Post by mivo on 2008-04-05
It could also be something outside of your control, i.e. ISP issues, routing problems. etc. I'd just wait a few hours before you start making changing to your system.

---

