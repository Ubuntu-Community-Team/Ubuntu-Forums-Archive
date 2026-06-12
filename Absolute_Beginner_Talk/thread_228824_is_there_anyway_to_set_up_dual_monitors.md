---
title: "is there anyway to set up dual monitors?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by pap3rtiger on 2006-08-03
i have two 19in monitors on an nvidia card, any way to use them in ubuntu?

---

### Post by cantormath on 2006-08-03
> **pap3rtiger said:**
> i have two 19in monitors on an nvidia card, any way to use them in ubuntu?

I believe there are some nvidia tools in the repositories.
which Nvidia card do you have ?

With that said, the problem with the nvidia-glx package in the ubuntu repositories is that it does not have a detection routine for the model of your nvidia (or whether you have a nvidia card at all) before installing anything.

A solution to that could be automatix.

Automatix tries to solve this problem by developing a sophisticated detection routine to install the correct drivers based on the make and model. That said, its not a 100% perfect but its very close to being perfect.

Here are the directions to install it on dapper and breezy.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

There is also Automatixbleeder.

This installs a version of Automatix which installs bleeding edge and limited support software on Ubuntu, Kubuntu and Xubuntu Dapper.  You can have them both installed at the same time.
Here are the directions to installing it on dapper and breezy.

[http://ubuntuforums.org/showthread.php?t=225967](http://ubuntuforums.org/showthread.php?t=225967)

Arnieboy, one of the automatix developers just said to me when I asking  what the difference was between the Nvidia drivers in Automatix vs. Automatixbleeder:

" same as in automatix. Having said that, the nvidia function underwent a revision in version 6.4-4 of Automatix main. The next version of Automatix Bleeder will be brought up to sync with the main automatix code."



Note:
When using these apps, it will ask you when you are done if you want to restore the original sources.list, say yes.

---

