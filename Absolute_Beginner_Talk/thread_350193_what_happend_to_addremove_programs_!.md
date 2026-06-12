---
title: "what happend to add/remove programs ?!"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-01-31
hello all 

when i want to intsall anew software from add/remove programes i got this errors ! 

when i want to install Kmess :-
Cannot install 'kmess'

This application conflicts with other installed software. To install 'kmess' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

whem i want to install any thing kopete or vlc player or any thing :-
Cannot install 'amsn'

This application conflicts with other installed software. To install 'amsn' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

what is the problem

---

### Post by ashmew2 on 2007-01-31
have you tried runing this command in terminal ;
sudo aptitude install PACKAGENAME

I think that shud do the trick , plz paste the output

---

### Post by aysiu on 2007-01-31
When you have conflicting packages, it usually means you have conflicting repositories in your sources.list.

Get a fresh list by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again.

---

