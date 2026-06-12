---
title: "need help with unbutu on my imac"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by andychrist on 2006-03-02
Hello all
im both new to ubuntu and to imac's,so this might just be a me thing?
i had an imac given to me,but somehow i managed to lock myself out of osx (forgot my username) im a avid pc user so the mac is a project. got ubntu insalled,no real prob's,however anytime i try to network it to my pc i keep getting an error " failed to run network-admin as user root: child terminated with 1 status":mrgreen: can anyone give any hints/help pls?? Also i can't configure the network without getting the same error :cry: Thanks

---

### Post by glug101 on 2006-03-02
Hello Andy!  Welcome to the flock!

1st, if you forget your passwd in OSX (any account, including root) booting with an OSX install cd/dvd gives you the option to reset your passwd.  (out of luck if you don't have one;))

2nd, are you getting a prompt for a passwd in Ubuntu when you try to get into network configuration tool? (I forget what it's called)  The passwd that Ubuntu most asks for is your own.  It uses sudo (much like mac) to give ordinary users most of the superuser abilities.  All you should need to know is the passwd for the account that you are logged into.

Hope this helps! :D

---

### Post by andychrist on 2006-03-03
Thanx glug, i was outta luck with an osx cd/dvd:evil: ,but managed to get around most of my problems with a reinstall of ubuntu (forgot to plug in the network cable...D'OH):-# .Its up and running now,talks to my pc,can get on the net with it and email,so i`m well pleased with myself for that,but i've yet to figure out how to install packages that don't use synaptic (ie updates for amsn):-k. I'm totally new to linux/unix,well apart from some mac use,so any help/advice would be greatly appricatted. Thanks for your reply\\:D/

---

### Post by glug101 on 2006-03-03
Someone else who is actually running Ubuntu right now but know this off the top of their head, and the solution to installing random packages is different in each linux flavor.  For Debian flavored Linux (which includes Ubuntu) I think the install includes the dpkg command.  Look that up in a terminal by typing:
```
man dpkg
```

or just type in 'debian package install' into google or yahoo and see what comes up.  

I'd do it for you, but my last x86 computer just kicked the bucket, and I currently have a legal copy of os 10.4, and there is precious little that can be done in Ubuntu that cannot be done on osx.  (Ubuntu is just MUCH easier to install linux programs on ;))

---

