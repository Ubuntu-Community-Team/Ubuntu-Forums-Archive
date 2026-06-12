---
title: "Can't open Synaptic in Ubunutu 6.06"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by BusSys on 2007-03-26
I have installed apache on my Ubuntu 6.06 install.  Whilst trying to get it right I tried a lot of different things and as a result my apache works fine but i am unable to open Synaptic package manager.

Can anyone please advise if it is possible to re-install? or to restore to a previous point?

Thankyou.

---

### Post by taurus on 2007-03-26
What happens when you run this command from a terminal?

```
gksudo synaptic
```
Otherwise, try

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by BusSys on 2007-03-26
Great.

gksudo synaptic opens it fine

I am still unable to open synaptic (and some other applications) through system - admin - synaptic

Havent tried 

sudo aptitude update
sudo aptitude upgrade

yet.

---

