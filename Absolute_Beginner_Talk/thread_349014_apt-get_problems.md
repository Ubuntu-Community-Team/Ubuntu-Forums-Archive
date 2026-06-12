---
title: "apt-get problems"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by serid on 2007-01-29
Hi,

I'm completely new to apt-get. I have installed Eclipse and after that
whenever I install anything new, I get message, that one package is not fully installed or 
removed - sun-java5-doc. It says, that I need to download it manually.

The question is - how do I get rid of it so the next time I install something,
I won't have to type "no" <enter> ?

---

### Post by BarfBag on 2007-01-29
I'm pretty sure you type:

> sudo apt-get remove sun-java5-doc

If that doesn't work, go to Synaptic Package Manager (System - Administration), search for sun-java5-doc, and remove it from there.

---

### Post by Maestro23 on 2007-01-29
> **serid said:**
> Hi,

I'm completely new to apt-get. I have installed Eclipse and after that
whenever I install anything new, I get message, that one package is not fully installed or 
removed - sun-java5-doc. It says, that I need to download it manually.

The question is - how do I get rid of it so the next time I install something,
I won't have to type "no" <enter> ?

Noobie myself, but I believe:

#sudo apt-get remove <filename>

---

