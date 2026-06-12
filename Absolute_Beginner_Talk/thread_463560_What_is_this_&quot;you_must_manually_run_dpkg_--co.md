---
title: "What is this &quot;you must manually run dpkg --configure -a"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Grundalizer on 2007-06-03
When I try and add a new program from the add/remove program under application, i select what programs i want and then when i go to hit Ok an error comes up that says you must manually run dpkg --configure -a  

i have no idea what the heck it is talking about

---

### Post by taurus on 2007-06-03
Just open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by machoo02 on 2007-06-03
It means that you should open up a terminal, and type in```
sudo dpkg --configure -a
```For some reason, the packaging program had a problem installing some package/program, and that command will continue with the configuration of any pending packages/programs.

---

