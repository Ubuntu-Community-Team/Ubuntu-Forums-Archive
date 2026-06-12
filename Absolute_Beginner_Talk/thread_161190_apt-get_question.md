---
title: "apt-get question"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-04-16
I've got my system pretty well how I like it, how can I keep certain packages from upgrading?


P.S. I Loooovvvveee Ubuntu

---

### Post by gingermark on 2006-04-16
Do keep in mind that, assuming you don't enable backports, or any unofficial repositories, the only "upgrades" you will receive will be security updates. As such, I would highly recommend you don't stop upgrades.

However, to answer your question, run Synaptic Package Manager and select the package in question. Then, on the top menu click "Package" and select "Lock Version".

---

### Post by My-dial-up on 2006-04-16
What about in Terminal mode please?

---

### Post by utab on 2006-04-16
have a look at aptitude, I guess you want sth like that...

---

### Post by 5-HT on 2006-04-16
[quote=My-dial-up]What about in Terminal mode please?[/quote] 
Using aptitude : ```
 sudo aptitude hold <package> 
``` 
You'll probably have to install with aptitude for this to have effect, I'm not sure.

I prefer aptitude myself, but looking through both apt-get and dkpg man pages the following is what I could find.

Using apt-get or dpkg:
[quote= man dpkg]
dpkg --set-selections
     Set  package  selections  using file read from stdin.  This file
     should be in the format &#8217;<package> <state>&#8217;, where state is  one
     of  install,  hold, deinstall or purge.  Blank lines and comment
     lines beginning with &#8217;#&#8217; are also permitted. [/quote] 
A little searching through the man pages can go a long way:
```
 man <program> 
```

---

### Post by My-dial-up on 2006-04-16
Many thanks. All sorted now. Enjoyed playing with aptitude, didn't even know it existed!

---

