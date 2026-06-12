---
title: "Running Oracle 6i under Wine"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by scarmona on 2007-04-26
Hi people, I'm trying to run an Oracle 6i client using Wine to access my office's central server. Everything goes ok until a " Message file \ORANT\DBS\FMCUS.MSB not found"
When I run the program from windows XP I have no trouble at all.
I'm using Feisty btw.

Anyone have any information I can use to solve this?

Thanks

---

### Post by phr0ze on 2007-04-26
The oracle client is very dependent on the path statement configured during boot. Try to get the oracle parts of the  path statement from windows and tell wine to use it.

---

### Post by scarmona on 2007-04-26
Um, I'm really a newbie in this oracle stuff, in fact I just need to get it up and running for an office platform.
How do I get the oracle parts of the path statement? and how do I configure Wine to use them?
Thanks again

---

