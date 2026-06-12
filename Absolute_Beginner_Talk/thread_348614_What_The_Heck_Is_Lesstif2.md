---
title: "What The Heck Is Lesstif2?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by dmgreer on 2007-01-29
What the heck is lesstif2, and why is it unsatisfiable? I tried installing FreeWRL, and all it says is "Error: Dependency is not satisfiable." So what do I do about that?

---

### Post by dmgreer on 2007-01-29
Oh, and btw I already ran sudo apt-get install lesstif2 with the result "E: Couldnt find package lesstif2".

---

### Post by benuski on 2007-01-29
Have you enabled the universe and multiverse repositories?  

Edit your sources list by either going 

```
gksudo gedit /etc/apt/sources.list
```
and uncomment everything that starts with "deb".  Or, through synpatic, you can click on Settings->Repositories, and then check off the unverise and multiverse tabs.  

Make sure to do a "sudo apt-get update" before trying to install.

---

### Post by DirtDawg on 2007-01-29
[http://packages.ubuntu.com/edgy/libs/lesstif2](http://packages.ubuntu.com/edgy/libs/lesstif2)

---

### Post by crc_canada on 2007-03-25
> **dmgreer said:**
> What the heck is lesstif2, and why is it unsatisfiable? I tried installing FreeWRL, and all it says is "Error: Dependency is not satisfiable." So what do I do about that?

Hi dmgreer;

This may not help you now (I don't get here as often as I should - too much other work) but we did put instructions for Ubuntu 6.06 here:

[http://freewrl.sourceforge.net/ubuntu606.html](http://freewrl.sourceforge.net/ubuntu606.html)

and, I'd expect that in a week or two we'll have these updated for the latest Ubuntu/FreeWRL combo. (I have a colleague working on it...)

John Stewart
CRC Canada
[http://www.crc.ca/FreeWRL](http://www.crc.ca/FreeWRL)

---

