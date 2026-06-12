---
title: "version verification"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by rnvinc on 2008-03-04
Holy cowbeans I'm glad I finally found you guys.

I'm brand new to Ubuntu and learning sloooowly, so I'm gonna ask a very basic question before going any deeper.

Installation from the live cd....no problem.

In order to direct my questions correctly I need to know what version of Ubuntu I am actually running. The welcome screen says simply Ubuntu.

Where do I find my version info?

---

### Post by nhandler on 2008-03-04
The quickest way is to go into a terminal and enter
```
cat /etc/issue
```

That will give you the version number.
8.04=Hardy (Currently under Development and a LTS release)
7.10=Gutsy (Current Stable Release)
7.04=Feisty
6.10=Edgy
6.04=Dapper (Current Long Term Support Release)

---

### Post by rnvinc on 2008-03-04
Thanks a lot.

I have Ubuntu 7.10 /n /l 

Not sure what the /n /l is though.

---

### Post by nhandler on 2008-03-04
You can ignore the /n /l. It doesn't matter. And 7.10 (Gutsy) is the one you should probably stay on until Hardy is released in April.

For people interested in finding out their version of Ubuntu using a GUI, you can go to System->About Ubuntu. The second paragraph should say the version of Ubuntu you are running.

Here is what mine says

> Thank you for your interest in Ubuntu 7.10
                - the Gutsy Gibbon - released in October 2007.

---

