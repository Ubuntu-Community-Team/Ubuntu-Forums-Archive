---
title: "xubuntu slow problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-14
Hi im really new to xubuntu and i just installed it on my dell diemension 340 usin the alternate cd.It has 256mb of ram.My problem is that its slow at boot up,during my session and all the way to shut down.Is there any way to speed it up?

---

### Post by Inxsible on 2007-08-14
How slow is it?

Can you give us additional specs of the machine ?

---

### Post by Dionysus135 on 2007-08-14
well its like laggy slow and for some reason i cant find the system specs.

---

### Post by Inxsible on 2007-08-14
> **Dionysus135 said:**
> well its like laggy slow and for some reason i cant find the system specs.
System--> Administration-->System Monitor will give you all the system info.

---

### Post by Dionysus135 on 2007-08-14
yea when i go on system it doesnt say adminstration.

---

### Post by talby on 2007-08-14
What helped my slow pc with boot times, i used "boot up mananger" you can install it with "sudo apt-get install bum" then run "sudo bum" and you can disable select services you don't need (like bluetooth, MD raid, etc)

check out [Linux in Government: Optimizing Desktop Performance, Part III @ linuxjournal]("http://www.linuxjournal.com/comment/reply/8322") and scroll down to the ubuntu section for a rundown.

Be careful!  disabling the wrong thing can cause major problems.  Ask if you are not sure :)

---

### Post by ugm6hr on 2007-08-14
The suggestions here might help:
[http://ubuntuforums.org/showpost.php?p=3121072&postcount=43](http://ubuntuforums.org/showpost.php?p=3121072&postcount=43)

Otherwise, an alternative Desktop might help (e.g. icewm)

---

### Post by Dionysus135 on 2007-08-18
> **talby said:**
> What helped my slow pc with boot times, i used "boot up mananger" you can install it with "sudo apt-get install bum" then run "sudo bum" and you can disable select services you don't need (like bluetooth, MD raid, etc)

check out [Linux in Government: Optimizing Desktop Performance, Part III @ linuxjournal]("http://www.linuxjournal.com/comment/reply/8322") and scroll down to the ubuntu section for a rundown.

Be careful!  disabling the wrong thing can cause major problems.  Ask if you are not sure :)

I tried used the code "sudo apt-get install bum" but i got an error messege saying "Package bum is not available, but is referred to by another package.This may mean the package is missing, has been obseleted, or is only available from another source"

E:Package bum has no installation candidate.

---

