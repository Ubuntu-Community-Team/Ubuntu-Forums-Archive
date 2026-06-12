---
title: "i cannot find the rest of the software in kubuntu"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-01-29
hello all am using kubuntu and when iam going to add anew software i found that there are just a few packages of the software available however i checked the tow options !!!
and i cannot install any thing from there !!! when i was using ubuntu there was a punsh of software available more than kubuntu what is the problem ?

---

### Post by Skidlz on 2007-01-29
You need to find other sources. Use synaptic and source files. I guess its just a general lack of kde programs? I don't use kde so I don't know. 

Why don't you switch back to Ubuntu?

---

### Post by sardion on 2007-01-29
Make sure you have universe and multiverse enabled.  I seem to recall that kubuntu makes that harder than ubuntu does (the update manager/synaptic equivalent is less polished in kubuntu).

In a terminal, do 

cat /etc/apt/sources.list

and make sure the lines for universe and multiverse are uncommented (no # sign).  If they are commented, do a ksudo "whatever editor" /etc/apt/sources.list and remove them.

---

### Post by bustanil on 2007-01-29
Maybe you didn't set up your repositories correctly. run **adept_manager** program as root. Then go to menu View >  Manage Repositories. You'll see a list of repository locations. just enable the multiverse and universe repository, then click Fetch Updates button on the toolbar...

---

