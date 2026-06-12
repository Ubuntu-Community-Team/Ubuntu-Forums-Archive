---
title: "booting issue"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-05-11
Hello, the following question is mine: I want to know, where the config file lies in which all the programs are listed, that need booting, furthermore, is there for each program originally started a description, what it does. I ask this, cos I got the impression, that ubuntu starts too many processes, which i do not need. This impression is rooted in a look into the programs that run and which can be seen in the systems monitor. There are a lot of programs of which i think that they are unnecessary and waste the capacities of the computer. I'm sure there is a wiki to this topic. Can you tell me where it is?

Thanks, niko

---

### Post by louis_nichols on 2006-05-11
[This link]("http://doc.gwos.org/index.php/Reduce_boot") might help you.

[http://doc.gwos.org](http://doc.gwos.org) has all sorts of useful info for your ubuntu install. Good luck!

---

### Post by steve.horsley on 2006-05-11
I don't know of a good description of them, but all the "services" that get started are linked to from /etc/rc2.d. (Ubuntu always uses runlevel 2). Each link starts with Snn where nn is a two digit number. They are started in order, S00? first, S99? last. 

A useful tool is the package bum (sudo apt-get install bum) - then you can find System->Administration->Boot Up Manager. This gives a brief description of the services and allows you to start and stop them.

---

