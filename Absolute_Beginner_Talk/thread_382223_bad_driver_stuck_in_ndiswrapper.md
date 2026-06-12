---
title: "bad driver stuck in ndiswrapper"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by thejones on 2007-03-11
i have been trying to get my broadcom wireless card to work in 6.10, but i have run into a problem.

ndiswrapper seems to have a bad driver stuck in it. i have tried to deleted it, but this is what it what it shows me:

```
 
jones@jones-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
jones@jones-laptop:~$ ndiswrapper -e bcmwl5
jones@jones-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
jones@jones-laptop:~$

```

it just wont go away! i have tried everything that i know (which isnt much lol). i have unistalled ndiswrapper. i have unistalled and then shut down befor reinstalling it. ](*,) 

i need a "pulling out hair" smilie to go next to that one......

any ideas guys?

---

### Post by Ek0nomik on 2007-03-11
What commands have you ran to get rid of it?  Post your output, please.

This thread may not even directly correlate to your problem, but it helped me get rid of my driver when I needed to.  [http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092)

Post some output and hopefully I can try to help!

Cheers!

---

