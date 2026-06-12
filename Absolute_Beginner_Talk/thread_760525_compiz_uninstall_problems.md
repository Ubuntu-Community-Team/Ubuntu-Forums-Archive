---
title: "compiz uninstall problems"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by zeus123 on 2008-04-20
Im currently using xubuntu7.10 on a ppc.

I installed compiz and xgl using synaptic only to find my ati 9200 isnt up to the job. So I uninstalled both compiz and xgl to discover I dont have a window decorator working.

How can I get the default xubuntu decorator working?

Many Thanks for your help.
Rik

---

### Post by sayakb on 2008-04-20
Open a terminal and type:
```
xfwm4 --replace
```
You may create a startup launcher pointing to the command..

---

### Post by zeus123 on 2008-04-20
brilliant! worked a treat. Many Thanks!

---

### Post by sayakb on 2008-04-20
You're welcome :)
Please mark the thread as solved.

---

