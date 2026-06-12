---
title: "Add/remove doesn't work"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-08-07
Hello, I installed UBuntu 7.04 two days ago. When I try to install programs from add/remove in Applications it says Error occurred The following details are provided:
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E:_cache->open() failed, please report

When  I try to open synaptic it says the same thing.
When I try to run dpkg --configure -a it says:
dpkg: requested operation requires superuser privilege

What should I do?:(

---

### Post by overdrank on 2007-08-07
> **mikecomua said:**
> Hello, I installed UBuntu 7.04 two days ago. When I try to install programs from add/remove in Applications it says Error occurred The following details are provided:
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E:_cache->open() failed, please report

When  I try to open synaptic it says the same thing.
When I try to run dpkg --configure -a it says:
dpkg: requested operation requires superuser privilege

What should I do?:(

HI add sudo to that command in the terminal 
```
sudo dpkg --configure -a
```

---

### Post by mikecomua on 2007-08-07
What do you mean?

---

### Post by overdrank on 2007-08-07
> **mikecomua said:**
> What do you mean?

Use the command given in my post it then terminal located under applications, accessories, terminal and it will correct the errors  hopefully!

Edit make sure that synaptic and add and remove are closed before you use the terminal.

---

### Post by vexorian on 2007-08-07
some package manager crashed or halted when it was running.

Try following what it says, press alt+f2 and type 

```
gksu dpkg --configure -a
```

it shall ask your password.

edit: sorry when I began typing this was the only post.

---

### Post by asmoore82 on 2007-08-07
the reconfigure command must be run with root [admin] priviledge ... preface the command with 'sudo'

```
~ $ sudo dpkg --configure -a
```

enter Your user password at the prompt; you will get absolutely no feedback while entering the password;
this is completely normal. "Everybody falls the first time."

---

### Post by overdrank on 2007-08-07
> **asmoore82 said:**
> the reconfigure command must be run with root [admin] priviledge ... preface the command with 'sudo'

```
~ $ sudo dpkg --configure -a
```

enter Your user password at the prompt; you will get absolutely no feedback while entering the password;
this is completely normal. "Everybody falls the first time."

Good point forgot to add password would not be seen! :KS

---

### Post by mikecomua on 2007-08-07
Thanks!

---

