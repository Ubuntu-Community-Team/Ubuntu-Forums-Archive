---
title: "Running applications remotely via ssh -X: Leopard vs Ubuntu"
date: 2009-06-08
forum: Apple Hardware Users
---

### Post by ferdejuan on 2009-06-08
Hi everyone, I'd like to understand better how ssh works, with the idea of connecting from Ubuntu (Hardy) to Mac (Leopard) via ssh and running Mac applications remotely (and vice versa). My general question is: Can any application be run remotely? 

In general this works for me:

1) In Ubuntu, I do ssh -X -l myuser maccomputer.x.x.x
Then I can run, for example xcalc, and I see it in Ubuntu. However, more complex applications such as Safari or Mathematica do not run. If I have previously logged in the Mac as well, they start in the Mac after remotely calling them from Ubuntu. Otherwise I get the following error: 

_RegisterApplication(), FAILED TO establish the default connection to the WindowServer, _CGSDefaultConnection() is NULL.

2) In the Mac, I do the corresponding ssh and I can log in to Ubuntu. Surprisingly, I can run firefox, and even mathematica in this case. I can't, however, run wine (spotify under wine) for example. Same thing happens, if I was logged in Ubuntu before, I see them in Ubuntu, otherwise I get another error. 

I'd like to understand what's going on, but if there is a quick solution for running Mathematica as in point 1) is also very welcome. I have a Mac Pro for computing and I would like it to be used by more than just me, and also by myself remotely from home. 

Thanks for your help!

---

