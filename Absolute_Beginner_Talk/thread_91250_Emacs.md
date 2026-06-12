---
title: "Emacs???"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by gazruss on 2005-11-16
Hi again folks (kinda get the feeling i will saying that a lot in the next few months)

Anyway, i got my system running almost ok, i installed some apps from the synaptic manager, now i keep getting an error screen:-

E: emacs21 : subprocess post installation script returned error exit status 1
E: cedet-common: dependency problems - leaving unconfigured
E: eieio: dependency problems - leaving unconfigured
E: speedbar: dependency problems - leaving unconfigured

Any idea's

Thanks for the help so far received. My wife says i am obsessed in getting this laptop to work correctly.......

---

### Post by earobinson on 2005-11-16
when do you get this error, on boot, when you open a terminal, when you launch synaptic?

---

### Post by gazruss on 2005-11-16
i get the messege when i launch synnaptic

---

### Post by Kyral on 2005-11-16
```
sudo apt-get -f install
``` should fix'er right up

---

### Post by earobinson on 2005-11-16
you your install is broken, i think there is also a repair button in synaptic that you could use

---

