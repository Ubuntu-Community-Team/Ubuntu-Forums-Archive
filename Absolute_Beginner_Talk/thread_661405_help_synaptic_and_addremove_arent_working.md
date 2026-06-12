---
title: "help synaptic and add\remove arent working"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-07
help I use fiesty and synaptic and add\remove arent working they tell me to run a certain command and that command says i need super user privladges to run it Im new and I installed via wubi heeeeeeeeeelp

---

### Post by taurus on 2008-01-07
Applications -> Accessories -> Ternimal
```
**sudo** dpkg --configure -a
**sudo** apt-get update
```
Make sure you close down synaptic or Add/Remove first before you run those two commands.

---

### Post by niceguy123 on 2008-01-08
Wanted to send you a thanks for your help and just figured out how to do this.

---

### Post by exneo002 on 2008-01-08
I need super user power to run dkpg so how do I get super user ability

---

### Post by philinux on 2008-01-08
By using 

sudo

before the actual command

---

### Post by flamelab on 2008-01-08
And if you are bored typing sudo sudo sudo all the time , type once ( in the beginning )

```
sudo -s -H
```

and then you won't need to type sudo again .

That's a mini problem of ubuntu , because it has no super users as option ( aka **su** )but you do everything with temporary super users' commands (sudo instead of su )

---

### Post by exneo002 on 2008-01-08
thanx a billion does anybody else on this thread love rage against the machine were the renegades of ubuntu

---

### Post by exneo002 on 2008-01-08
hey I also need good ubunu avatars somthing cool 

and Im using fiesty to learn about ubuntu so should I try kubuntu 

and how do I install the wubi exe for 7.10 gutsy and hardy heron when it comes out
plus can I upgrad and save my desktop settings and programs

---

