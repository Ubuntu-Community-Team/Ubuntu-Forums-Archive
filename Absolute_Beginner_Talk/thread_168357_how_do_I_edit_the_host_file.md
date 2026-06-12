---
title: "how do I edit the host file?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by whateverwhenever on 2006-04-30
We got a big webapp here and would like to test it under linux. We downloaded ubuntu and are trying to change the host file. But having no experience whatsoever with linux we are not able to. 

Would anyone be so kind as to explain how to change the host file? We tried editing etc/hosts but it won't let us change anything.

TIA,

Steve.

---

### Post by jazzmuzik on 2006-04-30
GUI: gksudo gedit /etc/hosts
Command line: sudo vi /etc/hosts

Or 

[gk]sudo <your favorite editor> filename

---

### Post by whateverwhenever on 2006-04-30
no luck with either. 

The first one give me a blank file called host' (yes with an apostrophe at the end) and the term window indicates that some authentication error took place.

The second one pops open vi but seems to log me in as myself, not root (i can't change anything in the file)

---

### Post by jazzmuzik on 2006-04-30
It should be /etc/hosts not /etc/host

There is no root in Ubuntu. You use sudo and you give it your user password (in place of a root password) and it gives you temporary root permissions to execute the current command.

---

### Post by whateverwhenever on 2006-04-30
Well gksudo kept going on about some session protocol not being recognized, so I just typed 'sudo gedit /etc/hosts' and it worked :D

---

### Post by RebelwithoutaClue on 2008-03-11
That worked for me too,

Thanks.

:)

---

