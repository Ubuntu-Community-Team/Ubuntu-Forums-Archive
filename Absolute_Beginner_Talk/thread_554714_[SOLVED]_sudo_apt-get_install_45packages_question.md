---
title: "[SOLVED] sudo apt-get install 45packages question"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Greslore on 2007-09-19
I have used "sudo apt-get -y install package1 package2 package3 package4" without any problems.  Is there a limit to how many packages I can install at once?  I want to create a software install script with about 50 packages in total.

---

### Post by asmoore82 on 2007-09-19
the only limit is the string size limit of all command lines ...
the limit is at worst 32 thousand characters(max of 1 **signed short[16-bit] integer**)
but is probably even more than that on modern systems(**unsigned short[16-bit] integer** or **word[32-bit]**).

I've never had a problem:
keeping in mind that the ``*'' wildcard is expanded by the shell before executing the command,
you can test the limits with variations of an ``echo *'' command,
on my system, even this does not cause a problem:
```
~$ echo /*/*/*
```

P.S. ``echo /*/*/*/*'' takes a little bit of time to complete but still does not reach the limit.

---

### Post by Greslore on 2007-09-19
Ahh ok.  Thank you kindly! :)

---

