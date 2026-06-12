---
title: "whats root account? am I using one right now?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-04-22
I got scared by all those warnings to never use a root account. Is that the account first created while I was installing? or is it a hidden one that I don't have to worry about? Does my current account have the same privileges as the root account? Should I make a new account?

---

### Post by Campingman on 2007-04-22
To log in as root from the log on screen you need to type root as the user name.  
Log on as root is disabled by default so you should be OK.

---

### Post by Gmbrdilos on 2007-04-22
what about the account that I use now? (the one that I created during install)
does it have the same power as root? should I make a new one?

---

### Post by bobplano on 2007-04-22
> **Gmbrdilos said:**
> I got scared by all those warnings to never use a root account. Is that the account first created while I was installing? or is it a hidden one that I don't have to worry about? Does my current account have the same privileges as the root account? Should I make a new account?

the reason most people advise against using root is because you can really mess up your system pretty easily. the account that you made at the beggining is an "admin" account or an account that can use sudo which has the same powers at root but only for the commands you use sudo with. you shouldn't have to worry about root too much because it is disabled by default

---

### Post by aysiu on 2007-04-22
There is no root account, but the first account belongs to the *admin* group and can, at certain times, assume temporary root privileges for certain tasks.

More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

