---
title: "error when removing somthing in the synaptic"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-11-14
E: emifreq-applet: subprocess post-installation script returned error exit status 2

i got this error when removing some of the stuff i have found and either didn't understand just yet or wasn't what i want , what does it mean should i be worried?

---

### Post by Partyboi2 on 2007-11-14
Try:
(To remove)
```
sudo dpkg -r emifreq-applet
``````
 sudo aptitude update
``````
 sudo aptitude upgrade
```:)

---

