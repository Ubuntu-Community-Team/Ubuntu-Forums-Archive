---
title: "asterisk make error"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by psergiu on 2007-12-26
hi,
i am trying to install asterisk 1.4.14 and i get the following error at configure:

     configure: error: *** termcap support not found

and make doesn't work:
  
     **** The configure script must be executed before running 'make'.
     ****               Please run "./configure".
     ****
     make: *** [makeopts] Error 1

what's wrong???

---

### Post by overdrank on 2007-12-26
> **psergiu said:**
> hi,
i am trying to install asterisk 1.4.14 and i get the following error at configure:

     configure: error: *** termcap support not found

and make doesn't work:
  
     **** The configure script must be executed before running 'make'.
     ****               Please run "./configure".
     ****
     make: *** [makeopts] Error 1

what's wrong???

HI and have you install build essentials? This link may help
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by Ziria on 2008-01-29
I suppose this might be a bit too late, but just in case someone does stuble apon this post as I did.

Solution:
aptitude install bison flex libncurses5-dev build-essential

---

### Post by borisbos on 2008-02-16
Installing just installing libncurses5-dev trough synaptic Package manager did the job.
Thanks for the tip.
Boris

---

