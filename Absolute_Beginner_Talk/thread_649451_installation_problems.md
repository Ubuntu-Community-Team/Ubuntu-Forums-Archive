---
title: "installation problems"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by VandalHaven on 2007-12-24
I recently tried to install a program and then had to quit in the middle of the installation now whenever i try to update or install something i get an error saying

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

or one saying

only one software management tool is allowed to run at the same time
close other app first eg synaptic, aptitude

what can i do to be able to install things again
thanks

---

### Post by ~LoKe on 2007-12-24
Try this in the terminal
```
sudo killall synaptic
sudo dpkg --configure -a
```

---

### Post by VandalHaven on 2007-12-25
that didn't help and now i get an  error when trying to update saying SOFTWARE INDEX IS BROKE and it tells me to use synaptic or 

run sudo apt-get install -f 

and doing that doesn't help either

---

### Post by John.Michael.Kane on 2007-12-25
> **VandalHaven said:**
> that didn't help and now i get an  error when trying to update saying SOFTWARE INDEX IS BROKE and it tells me to use synaptic or 

run sudo apt-get install -f 

and doing that doesn't help either
First make sure synaptic is closed, As well as any other gui update tools

Then try.
```
sudo apt-get autoremove
```
Followed by
```
sudo apt-get autoclean
```

Then re try these steps.
1) ```
sudo dpkg --configure -a
```

2) ```
sudo aptitude -f remove
```
Retry configuring all packages that are un-configured 
3) ```
sudo dpkg --configure -a
```

Another option is to manually remove the offending package, and dependencies.
```
sudo aptitude remove -f packageA 
```
removing items in question until there is no more dependency problems.

---

### Post by VandalHaven on 2007-12-25
when i go into terminal it won't let me type or paste my password into it

---

