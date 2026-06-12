---
title: "Software index is broken"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2008-03-01
When i clicked on the orange box with a star burst in it on the top right-hand side of the tool bar, the Update Manager open but a message appeared that informed me that:

_Software index is broken _
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install - f" in a terminal to fix this issue first.

But when i did open a terminal as "root" and then entered "apt-get install - f" everything appeared to be alright until l i saw, E: Could find package f

Could someone tell me how i can resolve this problem please. Thanks all

---

### Post by jeffus_il on 2008-03-01
try:
```
sudo aptitude update
```
and then 
```
sudo aptitude upgrade
```
and post any error output

---

### Post by spiderbatdad on 2008-03-01
make sure sources are available under System>>Administration>>Software Sources. Then try again.```
sudo apt-get -f install
sudo apt-get update
```

---

### Post by jan quark on 2008-03-01
you must be very careful what you type in linux  

there no space between    -    and      f

the correct command is

```

sudo apt-get install -f
```

---

### Post by oscarthefish on 2008-03-01
Have opened terminal as "root" and entered "apt-get install -f" and everything now seems to be alright. Thanks for the help folks

---

