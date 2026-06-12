---
title: "I get this error message when I open Synaptic"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by bastonal on 2008-01-28
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was down loading Java, power went out and I keep getting this message....I don't have clue where to go and how to fix it.

When I open up Terminal - the same error message that I receive in synaptic -": dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report."- is also running in Terminal over and over and it doesn't stop just keeps rolling on!

Anyone?

---

### Post by jan quark on 2008-01-28
I am not that experienced yet with such problems so perhaps you wait for a geek to answer but 
why not do what synaptic says to you 

try running 
```
dpkg --configure -a
```
in the terminal

but wait for someone other to correct me, I dont want to nuke your PC:)

---

### Post by r4ik on 2008-01-28
It is,

sudo dpkg --configure -a

Just a word,but makes the difference. :)

---

### Post by bastonal on 2008-01-28
I'm not sure what you mean....paste what you wrote, ('sudo dpkg --configure -a') into "Terminal" and then hit enter?

When I do  open up Terminal - the same error message that I receive in synaptic -"*: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report."*-  is also running in Terminal over and over and it doesn't stop just keeps rolling on! 

Double help!

---

### Post by r4ik on 2008-01-28
Not sure what you are saying here if you copy and paste the command as is (without Qoutes) it should take care of it.
It should ask for you're passwrd hit enter again and you should be oke.

---

